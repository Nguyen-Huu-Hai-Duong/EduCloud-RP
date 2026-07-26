---
title : "Thiết lập Amazon S3"
date : 2026-07-26
weight : 2
chapter : false
pre : " <b> 5.3.2. </b> "
---

#### Vì sao dùng S3

EduCloud Lite cho phép Instructor tải lên ba loại file cho khóa học: **ảnh thumbnail**, **tài liệu bài học** và **video bài giảng**. Ở chế độ local, các file này nằm trong `backend/uploads` — không phù hợp khi deploy vì ổ đĩa của server không bền vững/không chia sẻ được giữa nhiều instance. Chuyển sang lưu ở **Amazon S3** giải quyết vấn đề này.

*(Chèn ảnh chụp màn hình các bước tạo bucket/upload thực tế của bạn vào các vị trí `![...]` bên dưới.)*

#### Bước 1 — Tạo bucket S3

1. Vào **S3 → Create bucket**, đặt tên duy nhất toàn cầu, ví dụ `educloud-lite-media-bucket`, chọn region trùng với `AWS_REGION` của backend (ví dụ `ap-southeast-1`).
2. Nếu muốn file (ảnh/video) truy cập trực tiếp qua URL công khai: bỏ chọn **Block all public access** và thêm bucket policy cho phép `s3:GetObject` công khai trên `arn:aws:s3:::<bucket-name>/*`. Nếu không, giữ bucket private và phục vụ file qua CloudFront/URL ký sẵn (nằm ngoài phạm vi workshop này).

![tạo bucket](/images/5-Workshop/5.3.2-S3-Upload/create-bucket.png)

#### Bước 2 — Cấu hình biến môi trường backend

```dotenv
AWS_ACCESS_KEY_ID=xxxxxxxxxxxxxxxxxxxx
AWS_SECRET_ACCESS_KEY=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
AWS_REGION=ap-southeast-1
AWS_S3_BUCKET_NAME=educloud-lite-media-bucket
AWS_S3_PUBLIC_BASE_URL=
UPLOAD_STORAGE=s3
```

Để trống `AWS_S3_PUBLIC_BASE_URL` nếu dùng URL mặc định dạng `https://<bucket>.s3.<region>.amazonaws.com`; điền vào nếu bucket đứng sau CloudFront/domain riêng.

#### Bước 3 — Luồng upload hoạt động thế nào

`s3_service.save_upload()` kiểm tra `UPLOAD_STORAGE`: nếu là `s3` thì gọi `_save_to_s3`, dùng `boto3` để `upload_fileobj` lên bucket với key dạng:

```
courses/{course_id}/{category}/{uuid}.{ext}
```

Bốn endpoint upload tương ứng, đều yêu cầu người gọi là **Instructor sở hữu khóa học** hoặc **Admin** (`require_course_owner_or_admin`):

| Endpoint | category | Định dạng cho phép | Giới hạn dung lượng |
| :--- | :--- | :--- | :--- |
| `POST /api/upload/course-thumbnail` | `thumbnails` | JPG/JPEG, PNG, WebP | 10 MB |
| `POST /api/upload/course-thumbnail/import` | `thumbnails` | JPG/JPEG, PNG, WebP (tải từ URL ngoài) | 10 MB |
| `POST /api/upload/lesson-material` | `materials` | PDF, DOC, DOCX, PPT, PPTX, TXT, ZIP | 50 MB |
| `POST /api/upload/video` | `videos` | MP4, WebM, MOV | 500 MB |

#### Nhập ảnh thumbnail từ URL ngoài

Ngoài việc tự tải file lên, Instructor có thể dán một URL ảnh có sẵn trên Internet để làm thumbnail khóa học. Backend (`remote_image_service.download_remote_image`) tải ảnh về giúp Instructor rồi lưu vào S3 qua cùng `save_upload()` ở trên — nhưng vì đây là request đi tải nội dung từ một URL do người dùng cung cấp, service này có thêm một lớp kiểm tra để chống **SSRF (Server-Side Request Forgery)**:

+ Chỉ chấp nhận URL `http`/`https`, không chứa username/password trong URL, chỉ cho phép cổng 80/443.
+ Resolve DNS của host và từ chối nếu bất kỳ địa chỉ IP nào không phải là **địa chỉ IP công cộng** (chặn truy cập vào `localhost`, mạng nội bộ, dải IP private) — ngăn Instructor lợi dụng tính năng này để dùng server làm bàn đạp quét/gọi vào hạ tầng nội bộ.
+ Redirect HTTP cũng bị kiểm tra lại theo cùng quy tắc trên (không tin tưởng URL đích sau khi redirect).
+ Sau khi tải xong, không chỉ tin `Content-Type` trả về mà còn kiểm tra **magic byte** đầu file để xác nhận đúng là ảnh JPEG/PNG/WebP.

#### Bước 4 — Kiểm thử

1. Đăng nhập vai trò Instructor, tạo một khóa học nháp.
2. Upload ảnh thumbnail, một tài liệu và một video cho bài học.
3. Mở S3 console, xác nhận object mới xuất hiện đúng đường dẫn `courses/<id>/thumbnails|materials|videos/...`.
4. Mở URL trả về từ response (field `url`) để xác nhận file truy cập được.

![kiểm tra object trên s3](/images/5-Workshop/5.3.2-S3-Upload/verify-object.png)

{{% notice note %}}
IAM policy gắn cho access key backend chỉ nên gồm `s3:PutObject`, `s3:GetObject` (và `s3:ListBucket` nếu cần) giới hạn trong `arn:aws:s3:::<bucket-name>` và `arn:aws:s3:::<bucket-name>/*` — không cấp quyền quản trị bucket cho runtime credential của ứng dụng.
{{% /notice %}}
