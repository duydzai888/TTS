# Shell variables
Trong chương này, chúng ta học cách quản lý các biến môi trường trong `shell`. Các biến này làcthường được các ứng dụng cần thiết.

## I. Ký hiệU dolar
Một ký tự quan trọng khác được giải thích bởi shell là ký hiệu đô la `$`. Shell sẽ trông cho một biến môi trường có tên như chuỗi theo sau ký hiệu đô la và thay thế nó với giá trị của biến (hoặc không có giá trị nào nếu biến không tồn tại).
Đây là một số ví dụ sử dụng `$HOSTNAME`, `$USER`, `$UID`, `$SHELL` và `$HOME`.
```
[root@laiduy ~]# echo day la $SHELL tren centos $HOSTNAME
day la /bin/bash tren centos laiduy
[root@laiduy ~]# echo ten nguoi dung cua may la $USER
ten nguoi dung cua may la root
```

## II. Trường hợp nhạy cảm
Ví dụ này cho thấy rằng các biến `shell` phân biệt chữ hoa chữ thường.
```
[root@laiduy ~]# echo Nguoi dung $USER da bong rat gioi
Nguoi dung root da bong rat gioi
[root@laiduy ~]# echo Nguoi dung $user da bong rat gioi
Nguoi dung da bong rat gioi
```

## III. Tạo biến
Ví dụ này tạo biến `$Tentoi` và đặt giá trị của nó. Sau đó, nó sử dụng `echo` để xác minh giá trị.
```
[root@laiduy ~]# Tentoi=Duy
[root@laiduy ~]# echo $Tentoi
Duy
```

## IV. Dấu ngoặc kép
Lưu ý rằng dấu ngoặc kép vẫn cho phép phân tích cú pháp các biến, trong khi dấu ngoặc kép ngăn cái này.
```
[root@laiduy ~]# echo "$Tentoi"
Duy
[root@laiduy ~]# echo '$Tentoi'
$Tentoi
```
`Bash shell` sẽ thay thế các biến bằng giá trị của chúng trong các dòng được trích dẫn kép, nhưng không phải trong các dòng đơn những dòng trích dẫn.
```
[root@laiduy ~]# echo "Hom nay $Tentoi da bong hoi non"
Hom nay Duy da bong hoi non
[root@laiduy ~]# echo 'Hom nay $Tentoi da bong hoi non'
Hom nay $Tentoi da bong hoi non
```

## V. Đặt
Bạn có thể sử dụng lệnh `set` để hiển thị danh sách các biến môi trường. Trên Ubuntu và
Hệ thống Debian, lệnh set cũng sẽ liệt kê các hàm `shell` sau các biến `shell`. Sử dụng thiết lập `|` để xem các biến sau đó.

## VI. Không đặt
Sử dụng lệnh `unset` để xóa một biến khỏi môi trường shell của bạn.
```
[root@laiduy ~]# unset Tentoi
[root@laiduy ~]# echo $Tentoi

[root@laiduy ~]#
```

## VII. $PS1 (chưa hiểu)
Biến `$PS1` xác định dấu nhắc trình bao của bạn. Bạn có thể sử dụng dấu gạch chéo ngược thoát đặc biệt các ký tự như `\u` cho tên người dùng hoặc `\w` cho thư mục làm việc. 
Trong ví dụ này, chúng tôi thay đổi giá trị của `$PS1` một vài lần.
















