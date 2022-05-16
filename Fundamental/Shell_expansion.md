# Shell expansion
## 1. Lệnh và tranh luận
Chương này giới thiệu cho bạn cách mở rộng trình bao bằng cách xem kỹ các lệnh và tranh luận. Biết mở rộng shell là rất quan trọng vì nhiều lệnh trên
Hệ thống Linux được xử lý và rất có thể bị thay đổi bởi shell trước khi chúng được thực thi.

Giao diện dòng lệnh hoặc trình bao được sử dụng trên hầu hết các hệ thống Linux được gọi là bash, là viết tắt của Bourne lại shell. Vỏ bash kết hợp các tính năng từ `sh` (bản gốc Bourne shell), `csh` (C Shell) và `ksh` (Korn Shell).

Chương này thường sử dụng lệnh `echo` để chứng minh các tính năng của shell. Lệnh `echo` rất đơn giản: nó lặp lại đầu vào mà nó nhận được.
```
[root@Centos7 ~]# echo LaiKhanhDuy
LaiKhanhDuy
```

### 1.1. Tranh luận
Một trong những tính năng chính của `shell` là thực hiện quét dòng lệnh. Khi bạn nhập một lệnh tại dấu nhắc lệnh của trình bao và nhấn phím enter, sau đó trình bao sẽ bắt đầu quét dòng đó, cắt nó thành các đối số. Trong khi quét dòng, shell có thể làm nhiều thay đổi đối với các đối số bạn đã nhập. Quá trình này được gọi là `shell expansion`. Khi trình bao hoàn tất quá trình quét và sửa đổi dòng đó, sau đó nó sẽ được thực thi.

### 1.2. Loại bỏ khoảng trắng
Các phần được phân tách bằng một hoặc nhiều khoảng trắng (hoặc tab) liên tiếp được coi là các đối số riêng biệt, mọi khoảng trắng bị xóa. Đối số đầu tiên là lệnh được thực thi, các đối số khác được cấp cho lệnh. Shell cắt của bạn một cách hiệu quả lệnh vào một hoặc nhiều đối số.
```
[root@Centos7 ~]# echo Lai Duy
Lai Duy
[root@Centos7 ~]# echo Lai        Duy
Lai Duy
[root@Centos7 ~]# echo Lai                      Duy
Lai Duy
```

Lệnh `echo` sẽ hiển thị từng đối số mà nó nhận được từ `shell`. Lệnh `echo` cũng sẽ thêm một khoảng trắng mới giữa các đối số mà nó nhận được.

### 1.3. Dấu nháy đơn
Bạn có thể ngăn chặn việc xóa các khoảng trắng bằng cách trích dẫn các khoảng trắng. Nội dung của chuỗi trích dẫn được coi là một đối số. Trong ảnh chụp màn hình bên dưới `echo` nhận được chỉ một đối số.
```
[root@Centos7 ~]# echo 'Lai Duy'
Lai Duy
[root@Centos7 ~]# echo 'Lai      Duy'
Lai      Duy
[root@Centos7 ~]# echo 'Lai            Duy'
Lai            Duy
```

### 1.4. Dấu ngoặc kép
Bạn cũng có thể ngăn chặn việc xóa các khoảng trắng bằng cách trích dẫn kép các khoảng trắng. Giống như ở trên, `echo` chỉ nhận một đối số.
```
[root@Centos7 ~]# echo "Lai            Duy"
Lai            Duy
```

### 1.5. echo và trích dẫn
Các dòng được trích dẫn có thể bao gồm các ký tự thoát đặc biệt được nhận dạng bởi lệnh `echo` (khi sử dụng `echo -e`). Ảnh chụp màn hình bên dưới cho thấy cách sử dụng `\n` cho dòng mới và `\t` cho `tab` (thường là tám khoảng trắng).
```
[root@Centos7 ~]# echo -e "Lai\nDuy"
Lai
Duy
[root@Centos7 ~]# echo -e "Lai \n Duy"
Lai
 Duy
[root@Centos7 ~]# echo -e "Lai \nDuy"
Lai
Duy
[root@Centos7 ~]# echo -e "Lai \n     Duy"
Lai
     Duy
```

```
[root@Centos7 ~]# echo -e "Lai \t Duy"
Lai      Duy
[root@Centos7 ~]# echo -e "Lai \tDuy"
Lai     Duy
[root@Centos7 ~]# echo -e "Lai\tDuy"
Lai     Duy
```
Lệnh `echo` có thể tạo ra nhiều hơn khoảng trắng, tab và dòng mới. 

## 2. Lệnh
### 2.1. type
Để tìm hiểu xem một lệnh được cung cấp cho shell được thực thi như một lệnh bên ngoài hay không hoặc như một lệnh nội trang, hãy sử dụng lệnh `type`.
```
[root@Centos7 ~]# type cd
cd is a shell builtin
[root@Centos7 ~]# type cat
cat is hashed (/usr/bin/cat)
```

Như bạn có thể thấy, lệnh `cd` là bên trong và lệnh `cat` là bên ngoài.
Bạn cũng có thể sử dụng lệnh này để hiển thị cho bạn biết lệnh đó có phải là bí danh hay không.
```
[root@Centos7 ~]# type ls
ls is aliased to `ls --color=auto'
```

### 2.2. Chạy các lệnh bên ngoài
Một số lệnh có cả phiên bản nội trang và phiên bản bên ngoài. Khi một trong các lệnh này được thực thi, phiên bản nội trang được ưu tiên. Để chạy phiên bản bên ngoài, bạn phải nhập đường dẫn đầy đủ đến lệnh.
```
[root@Centos7 ~]# type -a echo
echo is a shell builtin
echo is /usr/bin/echo
[root@Centos7 ~]# /bin/echo Running the external echo command...
Running the external echo command...
```

### 2.3. which
```
[root@Centos7 ~]# which ls cd mv rm mkdir
alias ls='ls --color=auto'
        /usr/bin/ls
alias mv='mv -i'
        /usr/bin/mv
alias rm='rm -i'
        /usr/bin/rm
/usr/bin/cd
/usr/bin/mkdir
```

## 3. Bí danh

### 3.1. Tạo các bí danh
`shell` cho phép bạn tạo bí danh. Bí danh thường được sử dụng để dễ nhớ hơn
tên cho một lệnh hiện có hoặc để dễ dàng cung cấp các tham số.
```
[root@Centos7 ~]# cat muahe.txt
Ngay 12/5/2022 co mua
Sap duoc di quan su
[root@Centos7 ~]# alias duy=tac
[root@Centos7 ~]# duy muahe.txt
Sap duoc di quan su
Ngay 12/5/2022 co mua
[root@Centos7 ~]# alias duy=cat
[root@Centos7 ~]# duy muahe.txt
Ngay 12/5/2022 co mua
Sap duoc di quan su
```

### 3.2. Viết tắt các lệnh
Bí danh cũng có thể hữu ích để viết tắt một lệnh hiện có.
```
[root@Centos7 ~]# alias .='ls -l'
[root@Centos7 ~]# ls -l
total 32
-rw-r--r--. 1 root root   72 May 12 15:21 all
-rw-------. 1 root root 1244 May 12 10:39 anaconda-ks.cfg
drwxr-xr-x. 2 root root  127 May 12 14:29 laiduy
-rw-r--r--. 1 root root   43 May 12 15:32 muahe.txt
-rw-r--r--. 1 root root   64 May 12 15:38 test1.txt
-rw-r--r--. 1 root root   26 May 12 15:17 test6.png
-rw-r--r--. 1 root root   20 May 12 15:20 test7.png
-rw-r--r--. 1 root root   26 May 12 15:20 test8.png
-rw-r--r--. 1 root root   38 May 12 15:25 txt.txt
[root@Centos7 ~]# .
total 32
-rw-r--r--. 1 root root   72 May 12 15:21 all
-rw-------. 1 root root 1244 May 12 10:39 anaconda-ks.cfg
drwxr-xr-x. 2 root root  127 May 12 14:29 laiduy
-rw-r--r--. 1 root root   43 May 12 15:32 muahe.txt
-rw-r--r--. 1 root root   64 May 12 15:38 test1.txt
-rw-r--r--. 1 root root   26 May 12 15:17 test6.png
-rw-r--r--. 1 root root   20 May 12 15:20 test7.png
-rw-r--r--. 1 root root   26 May 12 15:20 test8.png
-rw-r--r--. 1 root root   38 May 12 15:25 txt.txt
```

### 3.3. Tùy chọn mặc định
Bí danh có thể được sử dụng để cung cấp các lệnh với các tùy chọn mặc định. Ví dụ dưới đây cho thấy cách đặt tùy chọn `-i` mặc định khi nhập `rm`.
```
[root@Centos7 ~]# rm -i test8.png
rm: remove regular file ‘test8.png’? n
[root@Centos7 ~]# rm test8.png
[root@Centos7 ~]# ls test8.png
ls: cannot access test8.png: No such file or directory
[root@Centos7 ~]# touch test8.png
[root@Centos7 ~]# alias rm='rm -i'
[root@Centos7 ~]# rm test8.png
rm: remove regular empty file ‘test8.png’? n
```
Một số bản phân phối bật bí danh mặc định để bảo vệ người dùng khỏi việc vô tình xóa tệp (' `rm -i` ',' `mv -i` ',' `cp -i` ')

### 3.4. Xem bí danh
Bạn có thể cung cấp một hoặc nhiều bí danh làm đối số cho lệnh bí danh để lấy định nghĩa. Không cung cấp đối số sẽ cung cấp danh sách đầy đủ các bí danh hiện tại.
```
[root@Centos7 ~]# alias . l c
alias .='ls -l'
alias l='.'
alias c='clear'
```

### 3.5. Bỏ bí danh
Bạn có thể hoàn tác một `alias` bằng lệnh `unalias`.
```
[root@Centos7 ~]# which rm
alias rm='rm -i'
        /usr/bin/rm
[root@Centos7 ~]# unalias rm
[root@Centos7 ~]# which rm
/usr/bin/rm
```

## 4. Hiển thị shell expansion
Bạn có thể hiển thị mở rộng shell với `set -x` và ngừng hiển thị nó với `set + x`. Bạn có thể muốn sử dụng thêm điều này trong khóa học này hoặc khi nghi ngờ về chính xác `shell` là gì thực hiện với lệnh của bạn.
```
[root@Centos7 ~]# set -x
++ printf '\033]0;%s@%s:%s\007' root Centos7 '~'
[root@Centos7 ~]# echo $USER
+ echo root
root
++ printf '\033]0;%s@%s:%s\007' root Centos7 '~'
[root@Centos7 ~]# echo \$USER
+ echo '$USER'
$USER
++ printf '\033]0;%s@%s:%s\007' root Centos7 '~'
[root@Centos7 ~]# set +x
+ set +x
[root@Centos7 ~]# echo $USER
root
``` 