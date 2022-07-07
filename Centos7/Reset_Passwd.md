# Reset Password Windows - Ubuntu20 - Centos7
## Menu
[I. Reset Password Windows.](#reset-password-windows)
- [1. Đổi mật khẩU do nghi ngờ có người vào](#Win_doimatkhau)
- [2. Đổi do quên](#Win_doquen)

[II. Reset Password Ubuntu 20](#reset-password-ubuntu-20)
- [1. Đổi do nghi ngờ có người vào](#Ubuntu_doimatkhau)
- [2. Đổi do quên](#Ubuntu_doquen)
  
[III. Reset password Ubuntu 18](#reset_passwd_Ubuntu18)  
[IV. Reset Password Centos7](#reset-password-centos7)
- [1. Đổi do nghi ngờ có người vào](#Centos_doimatkhau)
- [2. Đổi do quên](#Centos_doquen)

[Tài liệu tham khảo](#Tai_lieu_tham_khao)



<a name="reset-password-windows"></a>
## I. Reset Password Windows.

<a name="Win_doimatkhau"></a>
#### 1. Đổi mật khẩu do nghi ngờ có người vào.
B1: Nhấn tổ hợp phím `Windows + R`.
B2: Nhập `control userpasswords2` và Enter.

![image](https://user-images.githubusercontent.com/84270045/166852529-49db5170-27f0-41df-8b6b-db629cc49853.png)

B3: Sau khi hiện ra bảng ta ấn theo gợi ý.

![image](https://user-images.githubusercontent.com/84270045/166852686-07e128c5-6729-44b6-b70e-fe835cd122cc.png)

B4: Chọn `change a password`.

![image](https://user-images.githubusercontent.com/84270045/166852981-89faba9e-0673-4e87-a64c-b137ad6d0990.png)

B5: Điền lại mật khẩu cũ và đặt mật khẩu mới cho User.

![image](https://user-images.githubusercontent.com/84270045/166853108-6fa12ed7-9626-4475-b13b-16ba6d680aaa.png)

<a name="Win_doquen"></a>
#### 2. Đổi do quên.

<a name="reset-password-ubuntu-20"></a>
### II. Reset Password Ubuntu 20.

<a name="Ubuntu_doimatkhau"></a>
#### 1. Đổi do nghi ngờ có người vào.
Ta sử dụng lệnh `passwd "tên user"`

![image](https://user-images.githubusercontent.com/84270045/166894009-15e66d9b-0c1a-47a1-a9c2-008afbe428b4.png)

Ta tiến hành nhập lại mật khẩu cũ và nhập mật khẩu mới.

<a name="Ubuntu_doquen"></a>
#### 2. Đổi do quên
Khởi động lại Ubuntu và giữ `Shift` cho đến khi xuất hiện bảng như hình dưới.

![image](https://user-images.githubusercontent.com/84270045/167057794-2ed17ed3-629d-4dbc-b32c-d4701af034fb.png)

Ấn `e` và sẽ xuất hiện nội dung như bên dưới.

![image](https://user-images.githubusercontent.com/84270045/167057884-2daf5e1d-147f-46f5-bcf9-7c2c94c94ffb.png)



Tìm đến dòng và thay thế như trong hình.

![image](https://user-images.githubusercontent.com/84270045/167058055-5a99b128-6d45-48c5-90b8-c9a874440da0.png)

![image](https://user-images.githubusercontent.com/84270045/167057107-04e2cbe2-de33-41da-99a1-59b77a1cafaa.png)

Sau khi sửa xong, ấn tổ hợp phím `Ctrl + x` hoặc `f10` để tiến hành boot.

Kiểm tra trạng thái của phân vùng gốc bằng lệNh `mount | grep -w /`
![image](https://user-images.githubusercontent.com/84270045/167057305-2314615a-edeb-464a-ae79-8f81dc68c8df.png)

Đặt lại mật khẩu cho root: `passwd laiduy`

![image](https://user-images.githubusercontent.com/84270045/167058879-179ecb23-3ad4-43fa-8134-328e895deae7.png)

Lưu và khởi động lại: `exec /sbin/itit`

<a name="reset_passwd_Ubuntu18"></a>

### III. Reset password Ubuntu 18
- Đổi do quên mật khẩu.
B1. Khởi động lại Ubuntu và giữ `Shift` cho đến khi xuất hiện bảng như bên dưới.
![reboot](Pictures/ubuntu.png)

B2. Ấn `e` để tiến hành chỉnh sửa. Sau khi ấn `e` sẽ xuất hiện nội dung như bên dưới.
![e](Pictures/e-ubuntu.png)

B3. Kéo xuống và sửa đổi nội dung như ảnh bên dưới.
![ro](Pictures/ro-ubuntu.png)

![rw](Pictures/rw-ubuntu.png)

Sau khi chỉnh sửa xong, ta ấn `Ctrl x` hoặc `F10` để khởi động lại hệ thống của bạn. Hệ thống của bạn sẽ khởi động vào màn hình root shell như hình dưới. Bạn có thể xác nhận rằng hệ thống tệp gốc có quyền truy cập đọc và ghi bằng cách chạy lệnh `mount | grep -w /`.
![root](Pictures/root.png) 

Bây giờ ta đã có thể đổi mật khẩu của user.
![change](Pictures/passwd.png)

Sau khi đổi xong, ta tiến hành khởi động lại `exec /sbin/init`.
Chờ khởi động lại xong và đăng nhập vào bằng mật khẩu mới.



<a name="reset-password-centos7"></a>
### IV. Reset Password Centos7

<a name="Centos_doimatkhau"></a>
#### 1. Đổi do nghi ngờ có người vào.

**Thực hiện như với Ubuntu 20**


<a name="Centos_doquen"></a>
#### 2. Đổi do quên.

Ta tiến hành khởi động lại Centos7 và khi hiện ra màn hình bên dưới ta nhấn phím `e`.


Sau đó sẽ xuất hiện ra nội dung như bên dưới. Ta nhấn phím mũi tên để kéo xuống dưới và tìm từ `ro` tại dòng `linux 16`.

![image](https://user-images.githubusercontent.com/84270045/167054106-776a3778-6c22-4451-be91-8da9341bb3eb.png)



Ta thay `ro` thành `rw init=/sysroot/bin/sh` và ấn `Ctrl + x` để lưu.

![image](https://user-images.githubusercontent.com/84270045/167055826-e21c707f-1469-4ac1-9e9a-aa2777e51bb1.png)


Ta tiến hành đặt lại mật khẩu tài khoản root. Gõ lệnh `chroot /sysroot` và `passwd root` để mount và đặt lại mật khẩU cho root. Sau khi thay mật khẩu cho root xong, ta gõ lần lượt các lệnh sau:
```
touch /.autorelabel
exit
reboot
```

![image](https://user-images.githubusercontent.com/84270045/167054370-811e8819-4df5-4e3a-8816-276e2711596f.png)







<a name="Tai_lieu_tham_khao"></a>
## Tài liệu tham khảo
- [Centos7](https://www.7host.vn/huong-dan-khoi-phuc-mat-khau-quan-tri-reset-root-password-tren-may-chu-su-dung-he-dieu-hanh-centos/#CentOS_7)

- [Ubuntu20](https://itsystems.vn/reset-password-on-ubuntu-20-04)
- [Ubuntu18](https://viettelco.vn/huong-dan-dat-lai-mat-khau-root-da-quen-trong-ubuntu/)
- [Windows](https://trainghiemso.vn/cach-lay-lai-mat-khau-windows-10-de-dang-nhat/?fbclid=IwAR1wYwpAfNVqeZVS72O2yKHM3wreepC7RtzjL1TrmwKRplW9ghQkkL0b39I)

**Tài liệu tham khảo chung:** Github [anh Huy](https://github.com/huydv398/Linux-tutorial/blob/15ca6a0dedad74a533259b28948cb136d8b26e2f/tool/Reset-passwd.md)