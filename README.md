# 5_TOKEN_AUTH

## Register 

**Register thành công**

Trong postman , chọn POST và nhập URL: http://localhost:3000/api/auth/register

Mở tab body -> raw json -> nhập thông tin đăng ký : {
  "username": "hao",
  "email": "hao@gmail.com",
  "password": "123456"
} 

Send -> Trả về : { "message": "User registered successfully!" }

<img width="1198" height="901" alt="image" src="https://github.com/user-attachments/assets/26d648f1-d976-45c1-bafe-81057e17e44d" />

User được lưu vào trong mongoDB , DB tokenAuthApp trong collection users:

<img width="1774" height="995" alt="image" src="https://github.com/user-attachments/assets/23b44f19-c1fc-430f-8448-f3f93fe3e176" />


**Register thất bại ( Trùng username,email )**:

<img width="1201" height="896" alt="image" src="https://github.com/user-attachments/assets/3c35f04b-4f24-45b7-9a1a-a40314b50765" />

<img width="1228" height="902" alt="image" src="https://github.com/user-attachments/assets/49b95aca-d390-4e60-ba39-4067f9627407" />


**Thiếu username, email**

<img width="1250" height="866" alt="image" src="https://github.com/user-attachments/assets/09160747-31a5-48ed-bae3-fe7e0b5e3f11" />

<img width="1243" height="880" alt="image" src="https://github.com/user-attachments/assets/8ec27b3c-015f-466c-9e9a-a943461c5a9f" />


## LOGIN

**LOGIN THÀNH CÔNG**

Trong Postman, chọn POST và nhập URL: http://localhost:3000/api/auth/login, trong tab body -> raw json -> nhập thông tin đăng nhập(theo thông tin vừa register): {
  "username": "hao",
  "email": "hao@gmail.com",
  "password": "123456"
}

Nhấn Send ->> Trả về, nhận về token: 

<img width="1250" height="921" alt="image" src="https://github.com/user-attachments/assets/5ae7b1cd-2354-4ddc-a147-9176c47c4a31" />

Cookie được lưu:

<img width="1120" height="798" alt="image" src="https://github.com/user-attachments/assets/fb409418-f030-46c4-90f8-08c84b15ce22" />

**LOGIN THẤT BẠI**

**Email không tồn tại**

Nhập sai email lúc register

<img width="1240" height="841" alt="image" src="https://github.com/user-attachments/assets/747dbe46-7d6b-439d-9644-18203991ea47" />


**Sai mật khẩu**

<img width="1256" height="937" alt="image" src="https://github.com/user-attachments/assets/647e41fa-536b-419f-a2dc-102cf2702bfa" />


## PROFILE

**TH1 – Truy cập thành công với token hợp lệ**

GET http://localhost:3000/api/auth/profile

Trong tab header, chọn Auth -> Auth Type = Bearer Token -> Nhập <token từ bước login> vào trường **Token**

<img width="1196" height="865" alt="image" src="https://github.com/user-attachments/assets/39190c77-4a0d-4619-a658-8d4401658ebc" />

Kết quả:

<img width="1250" height="894" alt="image" src="https://github.com/user-attachments/assets/0b1d6792-2a17-481d-82ce-b1d75e92e2b7" />


**TH2 – Không gửi token**

Không có header Authorization.

<img width="1258" height="874" alt="image" src="https://github.com/user-attachments/assets/dc1cb4c6-31c6-4ae3-9e77-ddc5e9c68f1e" />



**TH3 – Token sai định dạng / bị chỉnh sửa**

Gửi header:

Authorization: Bearer abc123

<img width="1213" height="848" alt="image" src="https://github.com/user-attachments/assets/7e564389-5674-464e-a58c-1412e294c83b" />
