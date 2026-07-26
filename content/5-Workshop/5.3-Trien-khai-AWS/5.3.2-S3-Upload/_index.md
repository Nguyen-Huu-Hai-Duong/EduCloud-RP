---
title : "Setting up Amazon S3"
date : 2026-07-26
weight : 2
chapter : false
pre : " <b> 5.3.2. </b> "
---

#### Why S3

EduCloud Lite lets an Instructor upload three kinds of course files: a **thumbnail image**, **lesson materials**, and **lecture videos**. In local mode these files live under `backend/uploads` — not suitable once deployed, since the server's disk isn't durable or shared across instances. Moving storage to **Amazon S3** solves this.

*(Insert your own screenshots of the bucket creation/upload steps at the `![...]` placeholders below.)*

#### Step 1 — Create an S3 bucket

1. Go to **S3 → Create bucket**, pick a globally unique name, e.g. `educloud-lite-media-bucket`, in the same region as the backend's `AWS_REGION` (e.g. `ap-southeast-1`).
2. If you want files (images/videos) to be reachable directly via a public URL: uncheck **Block all public access** and add a bucket policy allowing public `s3:GetObject` on `arn:aws:s3:::<bucket-name>/*`. Otherwise, keep the bucket private and serve files through CloudFront/pre-signed URLs (outside the scope of this workshop).

![create bucket](/images/5-Workshop/5.3.2-S3-Upload/create-bucket.png)

#### Step 2 — Configure backend environment variables

```dotenv
AWS_ACCESS_KEY_ID=xxxxxxxxxxxxxxxxxxxx
AWS_SECRET_ACCESS_KEY=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
AWS_REGION=ap-southeast-1
AWS_S3_BUCKET_NAME=educloud-lite-media-bucket
AWS_S3_PUBLIC_BASE_URL=
UPLOAD_STORAGE=s3
```

Leave `AWS_S3_PUBLIC_BASE_URL` empty to use the default URL shape `https://<bucket>.s3.<region>.amazonaws.com`; fill it in if the bucket sits behind CloudFront or a custom domain.

#### Step 3 — How the upload flow works

`s3_service.save_upload()` checks `UPLOAD_STORAGE`: when it's `s3`, it calls `_save_to_s3`, which uses `boto3` to `upload_fileobj` to the bucket with a key of the form:

```
courses/{course_id}/{category}/{uuid}.{ext}
```

Four upload endpoints in total, all of which require the caller to be the **Instructor who owns the course** or an **Admin** (`require_course_owner_or_admin`):

| Endpoint | category | Allowed formats | Size limit |
| :--- | :--- | :--- | :--- |
| `POST /api/upload/course-thumbnail` | `thumbnails` | JPG/JPEG, PNG, WebP | 10 MB |
| `POST /api/upload/course-thumbnail/import` | `thumbnails` | JPG/JPEG, PNG, WebP (fetched from an external URL) | 10 MB |
| `POST /api/upload/lesson-material` | `materials` | PDF, DOC, DOCX, PPT, PPTX, TXT, ZIP | 50 MB |
| `POST /api/upload/video` | `videos` | MP4, WebM, MOV | 500 MB |

#### Importing a thumbnail from an external URL

Besides uploading a file directly, an Instructor can paste the URL of an image already on the Internet to use as a course thumbnail. The backend (`remote_image_service.download_remote_image`) downloads the image on the Instructor's behalf and then stores it in S3 through the same `save_upload()` above — but because this request fetches content from a user-supplied URL, the service adds an extra layer of protection against **SSRF (Server-Side Request Forgery)**:

+ Only accepts `http`/`https` URLs, rejects URLs containing a username/password, and only allows port 80/443.
+ Resolves the host's DNS and rejects the request if any resolved IP address is not a **public IP address** (blocking access to `localhost`, internal networks, and private IP ranges) — preventing the feature from being used as a stepping stone to scan or reach internal infrastructure.
+ HTTP redirects are re-checked against the same rules (the destination URL after a redirect is never trusted blindly).
+ After downloading, the response isn't trusted just by its `Content-Type` header — the file's leading **magic bytes** are also checked to confirm it really is a JPEG/PNG/WebP image.

#### Step 4 — Testing

1. Sign in as an Instructor, create a draft course.
2. Upload a thumbnail image, a material file, and a video for a lesson.
3. Open the S3 console and confirm new objects appear under `courses/<id>/thumbnails|materials|videos/...`.
4. Open the URL returned in the response (the `url` field) to confirm the file is reachable.

![verify object in s3](/images/5-Workshop/5.3.2-S3-Upload/verify-object.png)

{{% notice note %}}
The IAM policy attached to the backend's access key should only include `s3:PutObject`, `s3:GetObject` (and `s3:ListBucket` if needed) scoped to `arn:aws:s3:::<bucket-name>` and `arn:aws:s3:::<bucket-name>/*` — do not grant bucket-administration permissions to the application's runtime credentials.
{{% /notice %}}
