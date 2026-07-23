---
title : "Tạo App Client & kiểm tra bằng CLI"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.3.2 </b> "
---

#### Lấy thông tin App Client

1. Trong User pool vừa tạo, vào tab **App integration**, kéo xuống mục **App clients**. Click vào app client đã tạo ở bước trước (`educloud-lite-web-client`).

*(Chèn ảnh danh sách App clients)*

2. Ghi lại **Client ID**. Đây chính là giá trị sẽ điền vào `COGNITO_CLIENT_ID` (backend) và `VITE_COGNITO_CLIENT_ID` (frontend) ở phần 5.4. Vì đây là public client nên **không có Client secret** — đúng với cách `CognitoUserPool` phía frontend được khởi tạo chỉ với `UserPoolId` và `ClientId`.

*(Chèn ảnh chi tiết App client, khoanh vùng Client ID)*

#### Kiểm tra User Pool bằng AWS CLI

Trước khi đụng tới code EduCloud, hãy xác nhận User Pool hoạt động đúng bằng AWS CLI.

{{% notice warning %}}
App client mặc định chỉ bật sẵn 2 luồng xác thực `ALLOW_USER_SRP_AUTH` và `ALLOW_REFRESH_TOKEN_AUTH` — đủ cho SDK React (`amazon-cognito-identity-js` dùng SRP). Để test nhanh bằng CLI ở bước 3 dưới đây, cần bật thêm `ALLOW_ADMIN_USER_PASSWORD_AUTH`: vào App client vừa tạo → **Edit** → mục **Authentication flows** → tick **ALLOW_ADMIN_USER_PASSWORD_AUTH** → **Save changes**. Lưu ý: EduCloud thật (frontend React) **không dùng** luồng này, đây chỉ để tiện kiểm tra bằng CLI.
{{% /notice %}}

*(Chèn ảnh bật Authentication flows cho App client)*

1. Đăng ký thử một user (thay `<CLIENT_ID>` bằng Client ID vừa lấy):

```bash
aws cognito-idp sign-up \
  --client-id <CLIENT_ID> \
  --username cli-test@example.com \
  --password "Demo123!" \
  --user-attributes Name=name,Value="CLI Test User" \
  --region ap-southeast-1
```

2. Vì chưa xác nhận mã email, xác nhận user bằng quyền admin (mô phỏng việc nhập mã 6 số):

```bash
aws cognito-idp admin-confirm-sign-up \
  --user-pool-id <USER_POOL_ID> \
  --username cli-test@example.com \
  --region ap-southeast-1
```

3. Đăng nhập thử để lấy ID token:

```bash
aws cognito-idp admin-initiate-auth \
  --user-pool-id <USER_POOL_ID> \
  --client-id <CLIENT_ID> \
  --auth-flow ADMIN_USER_PASSWORD_AUTH \
  --auth-parameters USERNAME=cli-test@example.com,PASSWORD=Demo123! \
  --region ap-southeast-1
```

*(Chèn ảnh kết quả trả về IdToken/AccessToken/RefreshToken)*

Nếu lệnh trả về khối `AuthenticationResult` chứa `IdToken`, `AccessToken`, `RefreshToken` — User Pool và App Client đã hoạt động đúng. Bạn có thể xoá user thử nghiệm này trước khi qua phần tiếp theo:

```bash
aws cognito-idp admin-delete-user \
  --user-pool-id <USER_POOL_ID> \
  --username cli-test@example.com \
  --region ap-southeast-1
```

#### Tóm tắt

Bạn đã tạo thành công một Cognito User Pool và App Client, đồng thời xác minh bằng CLI rằng luồng đăng ký → xác nhận → đăng nhập → nhận token hoạt động đúng — đây chính là 3 thao tác mà `cognitoService.ts` phía frontend EduCloud sẽ gọi lại thông qua SDK ở phần tiếp theo.
