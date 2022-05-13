# Các câu lệnh Fundamental Linux


### I. Làm việc với thư mục
Mô-đun này là tổng quan ngắn gọn về các lệnh phổ biến nhất để làm việc với các thư mục: `pwd, cd, ls, mkdir và rmdir`. Các lệnh này có sẵn trên mọi Linux (hoặc Unix) hệ thống.

Mô-đun này cũng thảo luận về các đường dẫn tuyệt đối và tương đối và hoàn thành đường dẫn trong bash shell.
#### 1. pwd
Dấu hiệu bạn đang ở đây có thể được hiển thị bằng lệnh `pwd` (Print Working Directory).

Mở giao diện dòng lệnh (còn được gọi là thiết bị đầu cuối, bảng điều khiển hoặc xterm) và nhập pwd. Công cụ hiển thị thư mục hiện tại của bạn.

```
[root@localhost ~]# pwd
/root
```

#### 2. cd
Bạn có thể thay đổi thư mục hiện tại của mình bằng lệnh cd (Change Directory).
```
[root@Centos7 ~]# cd /var
[root@Centos7 var]# ls
adm  cache  crash  db  empty  games  gopher  kerberos  lib  local  lock  log  mail  nis  opt  preserve  run  spool  tmp  www  yp
```

##### 2.1. cd ~
`Cd` cũng là một phím tắt để quay lại thư mục chính của bạn. Chỉ cần nhập `cd` mà không có mục tiêu thư mục, sẽ đưa bạn vào thư mục chính của bạn. Gõ `cd ~` cũng có tác dụng tương tự.
```
[root@Centos7 var]# cd
[root@Centos7 ~]# pwd
/root
```

```
[root@Centos7 var]# cd ~
[root@Centos7 ~]# pwd
/root
```

##### 2.2. cd ..
Để đi đến thư mục mẹ (thư mục ngay phía trên thư mục hiện tại của bạn trong thư mục cây), gõ `cd ..`.

```
[root@Centos7 www]# pwd
/var/www
[root@Centos7 www]# cd ..
[root@Centos7 var]# pwd
/var
```

##### 2.3. cd -
Một phím tắt hữu ích khác với cd là chỉ cần gõ `cd -` để chuyển đến thư mục trước đó.
```
[root@Centos7 ~]# cd /var
[root@Centos7 var]# ls
adm  cache  crash  db  empty  games  gopher  kerberos  lib  local  lock  log  mail  nis  opt  preserve  run  spool  tmp  www  yp
[root@Centos7 var]# cd tmp
[root@Centos7 tmp]# pwd
/var/tmp
[root@Centos7 tmp]# cd -
/var
[root@Centos7 var]# pwd
/var
```

#### 3. Đường dẫn tuyệt đối và tương đối.
Khi nhập một đường dẫn bắt đầu bằng dấu gạch chéo `(/)`, thì gốc của cây tệp được giả định. Nếu bạn không bắt đầu con đường của mình với một dấu gạch chéo, thì thư mục hiện tại là điểm bắt đầu giả định.
Ví dụ bên dưới trước tiên hiển thị thư mục `/home/laikhanhduy` hiện tại. Từ bên trong này thư mục, bạn phải gõ `cd /home` thay vì `cd home` để chuyển đến thư mục `/home`.
```
[root@Centos7 laikhanhduy]# pwd
/home/laikhanhduy
[root@Centos7 laikhanhduy]# cd home
-bash: cd: home: No such file or directory
[root@Centos7 laikhanhduy]# cd /home
[root@Centos7 home]# pwd
/home
```

Khi ở trong `/home`, bạn phải nhập `cd laikhanhduy` thay vì `cd /laikhnhduy` để vào thư mục con `laikhanhduy` của thư mục `/home` hiện tại.

```
[root@Centos7 home]# pwd
/home
[root@Centos7 home]# cd /laikhanhduy
-bash: cd: /laikhanhduy: No such file or directory
[root@Centos7 home]# cd laikhanhduy
[root@Centos7 laikhanhduy]# pwd
/home/laikhanhduy
```

Trong trường hợp thư mục hiện tại của bạn là `root directory/`, thì cả `cd /home` và `cd home` sẽ đưa bạn vào thư mục `/home`.

```
[root@Centos7 /]# cd home
[root@Centos7 home]# pwd
/home


[root@Centos7 /]# cd /home
[root@Centos7 home]# pwd
/home
```

#### 4. Hoàn thành con đường
Phím tab có thể giúp bạn nhập một đường dẫn mà không bị lỗi. Nhập cd `/et` theo sau là phím Tab sẽ mở rộng dòng lệnh thành `cd /etc/`. Khi gõ `cd /Et` sau đó là phím Tab, sẽ không có gì xảy ra vì bạn đã gõ sai đường dẫn (chữ E viết hoa).
Bạn sẽ cần ít lần gõ phím hơn khi sử dụng phím Tab và bạn sẽ chắc chắn rằng mình đã nhập đường dẫn là chính xác.

#### 5. ls
Bạn có thể liệt kê nội dung của một thư mục với `ls`.
```
[root@Centos7 var]# ls
adm  cache  crash  db  empty  games  gopher  kerberos  lib  local  lock  log  mail  nis  opt  preserve  run  spool  tmp  www  yp
```

##### 5.1. ls -a
Một tùy chọn thường được sử dụng với `ls` là `-a` để hiển thị tất cả các tệp. Hiển thị tất cả các tệp có nghĩa là bao gồm các tệp ẩn. Khi tên tệp trên hệ thống tệp Linux bắt đầu bằng dấu chấm, nó được coi là một tệp ẩn và nó không hiển thị trong danh sách tệp thông thường.
```
[root@Centos7 var]# ls -a
.  ..  adm  cache  crash  db  empty  games  gopher  kerberos  lib  local  lock  log  mail  nis  opt  preserve  run  spool  tmp  .updated  www  yp
```

##### 5.2. ls -l
Nhiều khi bạn sẽ sử dụng các tùy chọn với `ls` để hiển thị nội dung của thư mục trong các định dạng khác nhau hoặc để hiển thị các phần khác nhau của thư mục. Gõ chỉ ls cung cấp cho bạn một danh sách các tệp trong thư mục. Gõ `ls -l` cho bạn một danh sách dài.
```
[root@Centos7 var]# ls -l
total 4
drwxr-xr-x.  2 root root    6 Apr 11  2018 adm
drwxr-xr-x.  6 root root   57 May 12 10:44 cache
drwxr-xr-x.  2 root root    6 Oct  1  2020 crash
drwxr-xr-x.  3 root root   34 May 12 10:29 db
drwxr-xr-x.  3 root root   18 May 12 10:29 empty
drwxr-xr-x.  2 root root    6 Apr 11  2018 games
drwxr-xr-x.  2 root root    6 Apr 11  2018 gopher
drwxr-xr-x.  3 root root   18 May 12 10:27 kerberos
drwxr-xr-x. 24 root root 4096 May 12 10:44 lib
drwxr-xr-x.  2 root root    6 Apr 11  2018 local
lrwxrwxrwx.  1 root root   11 May 12 10:26 lock -> ../run/lock
drwxr-xr-x.  7 root root  287 May 12 10:44 log
lrwxrwxrwx.  1 root root   10 May 12 10:26 mail -> spool/mail
drwxr-xr-x.  2 root root    6 Apr 11  2018 nis
drwxr-xr-x.  2 root root    6 Apr 11  2018 opt
drwxr-xr-x.  2 root root    6 Apr 11  2018 preserve
lrwxrwxrwx.  1 root root    6 May 12 10:26 run -> ../run
drwxr-xr-x.  8 root root   87 May 12 10:29 spool
drwxrwxrwt.  3 root root   83 May 12 10:44 tmp
drwxr-xr-x.  4 root root   33 May 12 10:44 www
drwxr-xr-x.  2 root root    6 Apr 11  2018 yp
```

##### 5.3. ls -lh
Một tùy chọn `ls` thường được sử dụng khác là `-h`. Nó hiển thị các con số (kích thước tệp) trong một con người hơn định dạng có thể đọc được. Cũng được hiển thị bên dưới là một số biến thể trong cách bạn có thể đưa ra các tùy chọn đến ls. 


```
[root@Centos7 var]# ls -lh
total 4.0K
drwxr-xr-x.  2 root root    6 Apr 11  2018 adm
drwxr-xr-x.  6 root root   57 May 12 10:44 cache
drwxr-xr-x.  2 root root    6 Oct  1  2020 crash
drwxr-xr-x.  3 root root   34 May 12 10:29 db
drwxr-xr-x.  3 root root   18 May 12 10:29 empty
drwxr-xr-x.  2 root root    6 Apr 11  2018 games
drwxr-xr-x.  2 root root    6 Apr 11  2018 gopher
drwxr-xr-x.  3 root root   18 May 12 10:27 kerberos
drwxr-xr-x. 24 root root 4.0K May 12 10:44 lib
drwxr-xr-x.  2 root root    6 Apr 11  2018 local
lrwxrwxrwx.  1 root root   11 May 12 10:26 lock -> ../run/lock
drwxr-xr-x.  7 root root  287 May 12 10:44 log
lrwxrwxrwx.  1 root root   10 May 12 10:26 mail -> spool/mail
drwxr-xr-x.  2 root root    6 Apr 11  2018 nis
drwxr-xr-x.  2 root root    6 Apr 11  2018 opt
drwxr-xr-x.  2 root root    6 Apr 11  2018 preserve
lrwxrwxrwx.  1 root root    6 May 12 10:26 run -> ../run
drwxr-xr-x.  8 root root   87 May 12 10:29 spool
drwxrwxrwt.  3 root root   83 May 12 10:44 tmp
drwxr-xr-x.  4 root root   33 May 12 10:44 www
drwxr-xr-x.  2 root root    6 Apr 11  2018 yp
```

#### 6. mkdir
Đi dạo quanh cây tệp Unix rất thú vị, nhưng còn thú vị hơn khi tạo các thư mục của riêng bạn với `mkdir`. Bạn phải cung cấp ít nhất một tham số cho `mkdir`, tên của thư mục mới được tạo ra. Hãy suy nghĩ trước khi nhập dấu `/`.

```
[root@Centos7 ~]# mkdir laiduy
[root@Centos7 ~]# cd laiduy
[root@Centos7 laiduy]# ls -lh
total 0
```

##### 6.1. mkdir -p
Lệnh sau sẽ không thành công, vì thư mục mẹ của `test` không
hiện hữu.
```
[root@Centos7 ~]# mkdir /yasuo/caoboi/dasac
mkdir: cannot create directory ‘/yasuo/caoboi/dasac’: No such file or directory
```

Khi được cung cấp tùy chọn `-p`, thì `mkdir` sẽ tạo các thư mục mẹ nếu cần.

```
[root@Centos7 ~]# mkdir -p /yasuo/caoboi/dasac
[root@Centos7 ~]# cd /yasuo
[root@Centos7 yasuo]# ls -lh
total 0
drwxr-xr-x. 3 root root 19 May 12 11:25 caoboi
[root@Centos7 yasuo]# cd caoboi
[root@Centos7 caoboi]# ls -lh
total 0
drwxr-xr-x. 2 root root 6 May 12 11:25 dasac
[root@Centos7 caoboi]# cd dasac
[root@Centos7 dasac]# pwd
/yasuo/caoboi/dasac
```

#### 7. rmdir
Khi một thư mục trống, bạn có thể sử dụng `rmdir` để xóa thư mục.

```
[root@Centos7 home]# ls
laikhanhduy
[root@Centos7 home]# rmdir laikhanhduy
[root@Centos7 home]# ls -lh
total 0
```

# 7. rmdir -p (chưa hiểu)
Và tương tự như tùy chọn `mkdir -p`, bạn cũng có thể sử dụng `rmdir` để loại bỏ đệ quy các thư mục.




```
[root@Centos7 ~]# rmdir /yasuo/caoboi/dasac
[root@Centos7 ~]# cd /yasuo
[root@Centos7 yasuo]# cd caoboi
[root@Centos7 caoboi]# ls -lh
total 0
```

### II. Làm việc với các tập tin
Trong chương này, chúng ta học cách nhận dạng, tạo, xóa, sao chép và di chuyển tệp bằng cách sử dụng các lệnh như `file, touch, rm, cp, mv` và `rename`.

#### 1. Tất cả các tệp đều phân biệt chữ hoa chữ thường
Các tệp trên Linux (hoặc bất kỳ Unix nào) đều phân biệt chữ hoa chữ thường. Điều này có nghĩa là `FILE1` khác với `file1` và `/etc/hosts` khác với `/etc/Hosts` (cái sau không tồn tại trên một Máy tính Linux).
Ảnh chụp màn hình này cho thấy sự khác biệt giữa hai tệp, một tệp có chữ `T` viết hoa, tệp kia với chữ thường `t`.
```
[root@Centos7 laiduy]# ls
test.txt  Test.txt
[root@Centos7 laiduy]# cat test.txt
Lai Khanh Duy 2002
[root@Centos7 laiduy]# cat Test.txt
Khong biet viet gi
```

#### 2. Mọi thứ đều là một tập tin
Thư mục là một loại tệp đặc biệt, nhưng nó vẫn là một tệp phân biệt chữ hoa chữ thường. Mỗi thiết bị đầu cuối cửa sổ (ví dụ: `/dev/pts/4`), bất kỳ đĩa cứng hoặc phân vùng nào (ví dụ `/dev/sdb1`) và mọi quy trình đều được thể hiện ở đâu đó trong hệ thống tệp dưới dạng tệp. Nó sẽ trở nên rõ ràng trong suốt khóa học này rằng mọi thứ trên Linux đều là một tệp.

#### 3. file
Tiện ích tệp xác định loại tệp. Linux không sử dụng các phần mở rộng để xác định loại tệp. Dòng lệnh không quan tâm đến việc một tệp kết thúc bằng `.txt` hay `.pdf`. Như một hệ thống quản trị viên, bạn nên sử dụng lệnh tệp để xác định loại tệp. Đây là một số ví dụ trên một hệ thống Linux điển hình.
```
[root@Centos7 laiduy]# file test.txt
test.txt: ASCII text
```
Lệnh tệp sử dụng một tệp ma thuật có chứa các mẫu để nhận dạng các loại tệp. Phép thuật tập tin nằm trong `/usr/share/file/magic`. Gõ phép thuật man 5 để biết thêm thông tin. Thật thú vị khi chỉ ra tệp `-s` cho các tệp đặc biệt như trong `/dev` và `/proc`.

```
[root@Centos7 ~]# file /dev/sda
/dev/sda: block special
[root@Centos7 ~]# file -s /dev/sda
/dev/sda: x86 boot sector; partition 1: ID=0x83, active, starthead 32, startsector 2048, 2097152 sectors; partition 2: ID=0x8e, starthead 170, startsector 2099200, 81786880 sectors, code offset 0x63
```

```
[root@Centos7 ~]# file /proc/cpuinfo
/proc/cpuinfo: empty
[root@Centos7 ~]# file -s /proc/cpuinfo
/proc/cpuinfo: ASCII text, with very long lines
```

#### 4. touch
##### 4.1. Tạo một tệp trống
Một cách dễ dàng để tạo một tệp trống là chạm vào. (Chúng ta sẽ thấy nhiều cách khác để tạo tệp sau này trong sách này.)
Ảnh chụp màn hình này bắt đầu với một thư mục trống, tạo hai tệp bằng cách `touch` và danh sách
các tệp đó.

```
[root@Centos7 laiduy]# touch file1
[root@Centos7 laiduy]# touch file2
[root@Centos7 laiduy]# touch file3
[root@Centos7 laiduy]# ls -l
total 8
-rw-r--r--. 1 root root  0 May 12 11:45 file1
-rw-r--r--. 1 root root  0 May 12 11:45 file2
-rw-r--r--. 1 root root  0 May 12 11:45 file3
```

#### 5. rm
##### 5.1. Loại bỏ vĩnh viễn
Khi bạn không cần tệp nữa, hãy sử dụng `rm` để xóa tệp đó. Không giống như một số giao diện người dùng đồ họa, dòng lệnh nói chung không có thùng rác hoặc thùng rác để khôi phục tệp. Khi nào bạn sử dụng `rm` để xóa một tệp, tệp đã biến mất. 

```
[root@Centos7 laiduy]# ls
file1  file2  file3  test.txt  Test.txt
[root@Centos7 laiduy]# rm test.txt
rm: remove regular file ‘test.txt’? y
[root@Centos7 laiduy]# ls
file1  file2  file3  Test.txt
```

##### 5.2. rm -i
Để tránh việc vô tình xóa tệp, bạn có thể nhập `rm -i`
```
[root@Centos7 laiduy]# ls
file1  file2  file3  Test.txt
[root@Centos7 laiduy]# rm -i Test.txt
rm: remove regular file ‘Test.txt’? n
[root@Centos7 laiduy]# ls
file1  file2  file3  Test.txt
```

##### 5.3. rm -rf
Theo mặc định, `rm -r` sẽ không xóa các thư mục không trống. Tuy nhiên `rm` chấp nhận một số các tùy chọn sẽ cho phép bạn xóa bất kỳ thư mục nào. Câu lệnh `rm -rf` nổi tiếng vì nó sẽ xóa bất kỳ thứ gì (với điều kiện bạn có quyền làm như vậy). Khi bạn là đã đăng nhập với quyền root, hãy rất cẩn thận với `rm -rf` (f có nghĩa là `force` và r có nghĩa là `recursive`) vì là root ngụ ý rằng các quyền không áp dụng cho bạn. Bạn có thể xóa toàn bộ hệ thống tập tin một cách tình cờ.

```
[root@Centos7 ~]# mkdir duy
[root@Centos7 ~]# rm duy
rm: cannot remove ‘duy’: Is a directory
[root@Centos7 ~]# rm -rf duy
[root@Centos7 ~]# ls duy
ls: cannot access duy: No such file or directory
```



#### 6. cp
##### 6.1. Sao chép một tập tin
Để sao chép một tệp, hãy sử dụng `cp` với một đối số nguồn và đích.

```
[root@Centos7 laiduy]# ls
file1  file2  file3  Test.txt
[root@Centos7 laiduy]# cp file1 file1.1
[root@Centos7 laiduy]# ls
file1  file1.1  file2  file3  Test.txt
```

##### 6.2. Sao chép vào một thư mục khác
Nếu đích là một thư mục, thì các tệp nguồn sẽ được sao chép vào thư mục đích đó.
```
[root@Centos7 laiduy]# mkdir khanhduy
[root@Centos7 laiduy]# cp Test.txt khanhduy
[root@Centos7 laiduy]# ls khanhduy/
Test.txt
```

# 6.3. cp -r (chưa hiểu)
Để sao chép các thư mục hoàn chỉnh, hãy sử dụng `cp -r` (tùy chọn -r buộc sao chép đệ quy tất cả các tệp trong tất cả các thư mục con).

##### 6.4. Sao chép nhiều tệp vào thư mục
Bạn cũng có thể sử dụng `cp` để sao chép nhiều tệp vào một thư mục. Trong trường hợp này, đối số cuối cùng (a.k.a. đích) phải là một thư mục.

```
[root@Centos7 ~]# touch test4.txt
[root@Centos7 ~]# touch test5.txt
[root@Centos7 ~]# touch test6.txt
[root@Centos7 ~]# cp test4.txt test5.txt test6.txt laiduy/
[root@Centos7 ~]# cd laiduy
[root@Centos7 laiduy]# ls
file1  file1.1  file2  file3  test4.txt  test5.txt  test6.txt  Test.txt
```

##### 6.5. cp -i
Để ngăn `cp` ghi đè lên các tệp hiện có, hãy sử dụng tùy chọn `-i` (để tương tác).

```
[root@Centos7 laiduy]# cp test5.txt test6.txt -i
cp: overwrite ‘test6.txt’? n
```

#### 7. rm

##### 7.1. Đổi tên file với mv
Sử dụng `mv` để đổi tên tệp hoặc di chuyển tệp sang thư mục khác

```
[root@Centos7 ~]# ls
anaconda-ks.cfg  laiduy  test4.txt  test5.txt  test6.txt
[root@Centos7 ~]# mv test4.txt test7.txt
[root@Centos7 ~]# ls
anaconda-ks.cfg  laiduy  test5.txt  test6.txt  test7.txt
```

##### 7.2. Đổi tên thư mục bằng mv
Lệnh `mv` tương tự có thể được sử dụng để đổi tên các thư mục.
```
[root@Centos7 ~]# ls -l
total 4
-rw-------. 1 root root 1244 May 12 10:39 anaconda-ks.cfg
drwxr-xr-x. 2 root root  127 May 12 14:29 laiduy
-rw-r--r--. 1 root root    0 May 12 14:29 test5.txt
-rw-r--r--. 1 root root    0 May 12 14:29 test6.txt
-rw-r--r--. 1 root root    0 May 12 14:27 test7.txt
[root@Centos7 ~]# mv laiduy khanhduy
[root@Centos7 ~]# ls -l
total 4
-rw-------. 1 root root 1244 May 12 10:39 anaconda-ks.cfg
drwxr-xr-x. 2 root root  127 May 12 14:29 khanhduy
-rw-r--r--. 1 root root    0 May 12 14:29 test5.txt
-rw-r--r--. 1 root root    0 May 12 14:29 test6.txt
-rw-r--r--. 1 root root    0 May 12 14:27 test7.txt
```

##### 7.3. mv -i
`Mv` cũng có công tắc `-i` tương tự như `cp` và `rm`. Ví dụ dưới cho thấy `mv -i` sẽ yêu cầu quyền ghi đè lên tệp hiện có.


### 8. Đổi tên
Lệnh đổi tên là một trong những trường hợp hiếm hoi mà cuốn sách Các nguyên tắc cơ bản về Linux phải phân biệt giữa các bản phân phối Linux. Hầu hết mọi lệnh trong phần cơ bản của cuốn sách này hoạt động trên hầu hết mọi máy tính Linux. Nhưng đổi tên là khác nhau.
Cố gắng sử dụng `mv` bất cứ khi nào bạn chỉ cần đổi tên một vài tệp.


##### 8.1. Đổi tên định dạng của tập tin
Đổi các file có định dạng `.txt` sang `.png`
```
[root@Centos7 ~]# ls
anaconda-ks.cfg  laiduy  test6.txt  test7.txt  test8.txt
[root@Centos7 ~]# rename .txt .png *txt
[root@Centos7 ~]# ls
anaconda-ks.cfg  laiduy  test6.png  test7.png  test8.png
```

Ví dụ thứ hai đổi tên tất cả các tệp (*) thay thế `test` bằng `Test`.
```
[root@Centos7 ~]# ls
anaconda-ks.cfg  laiduy  test6.png  test7.png  test8.png
[root@Centos7 ~]# rename test Test *
[root@Centos7 ~]# ls
anaconda-ks.cfg  laiduy  Test6.png  Test7.png  Test8.png
```

### III. Làm việc với nội dung tệp
Trong chương này, chúng ta sẽ xem xét nội dung của các tệp văn bản với `head, tail, cat, tac, more, less và strings`. Chúng ta cũng sẽ có một cái nhìn sơ lược về khả năng của các công cụ như `cat` trong command line.
#### 1. head
Bạn có thể sử dụng `head` để hiển thị mười dòng đầu tiên của tệp.
```
[root@Centos7 ~]# head /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
```
Lệnh `head` cũng có thể hiển thị `n` dòng đầu tiên của tệp.
```
[root@Centos7 ~]# head -5 /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
```
Và head cũng có thể hiển thị `n byte` đầu tiên.
```
[root@Centos7 ~]# head -c14 /etc/passwd
root:x:0:0:roo[root@Centos7 ~]#
```

#### 2. tail
Tương tự như `head`, lệnh `tail` sẽ hiển thị mười dòng cuối cùng của tệp.
```
[root@Centos7 ~]# tail /etc/passwd
operator:x:11:0:operator:/root:/sbin/nologin
games:x:12:100:games:/usr/games:/sbin/nologin
ftp:x:14:50:FTP User:/var/ftp:/sbin/nologin
nobody:x:99:99:Nobody:/:/sbin/nologin
systemd-network:x:192:192:systemd Network Management:/:/sbin/nologin
dbus:x:81:81:System message bus:/:/sbin/nologin
polkitd:x:999:998:User for polkitd:/:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
postfix:x:89:89::/var/spool/postfix:/sbin/nologin
apache:x:48:48:Apache:/usr/share/httpd:/sbin/nologin
```

Bạn có thể cho đuôi số dòng bạn muốn xem.
```
[root@Centos7 ~]# tail -4 /etc/passwd
polkitd:x:999:998:User for polkitd:/:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
postfix:x:89:89::/var/spool/postfix:/sbin/nologin
apache:x:48:48:Apache:/usr/share/httpd:/sbin/nologin
```

#### 3. cat
Lệnh `cat` là một trong những công cụ phổ biến nhất, nhưng tất cả những gì nó làm là sao chép đầu vào chuẩn vào đầu ra tiêu chuẩn. Kết hợp với vỏ, điều này có thể rất mạnh mẽ và đa dạng. Một vài các ví dụ sẽ cung cấp một cái nhìn thoáng qua về các khả năng. Ví dụ đầu tiên rất đơn giản, bạn có thể sử dụng
`cat` để hiển thị một tập tin trên màn hình. Nếu tập tin dài hơn màn hình, nó sẽ cuộn đến cuối.
```
[root@Centos7 ~]# ls
anaconda-ks.cfg  laiduy  Test6.png  Test7.png  Test8.png
[root@Centos7 ~]# cat Test6.png
File duy nhat co noi dung
```

##### 3.1. concatenate
`cat` là viết tắt của `concatenate`. Một trong những cách sử dụng cơ bản của `cat` là nối các tệp thành một tệp lớn hơn (hoặc hoàn thành) tệp.
```
[root@Centos7 ~]# cat test6.png test7.png test8.png
File duy nhat co noi dung
Cai nay cung co nha
Tat ca deu co noi dung :3
```

```
[root@Centos7 ~]# cat test6.png test7.png test8.png >all
[root@Centos7 ~]# cat all
File duy nhat co noi dung
Cai nay cung co nha
Tat ca deu co noi dung :3
```

##### 3.2. Tạo tệp
Bạn có thể sử dụng `cat` để tạo các tệp văn bản phẳng. Gõ lệnh `cat> Winter.txt` như được hiển thị trong ảnh chụp màn hình bên dưới. Sau đó, nhập một hoặc nhiều dòng, kết thúc mỗi dòng bằng phím enter. Để lưu lại ấn tổ hợp phím `Ctrl + d`
```
[root@Centos7 ~]# cat > txt.txt
file test thu
file test thu
chuc cac ban thanh cong
[root@Centos7 ~]# cat txt.txt
file test thu
file test thu
chuc cac ban thanh cong
```
Tổ hợp phím `Ctrl d` sẽ gửi `EOF` (End of File) đến quá trình đang chạy kết thúc lệnh `cat`.

##### 3.3. Điểm đánh dấu cuối tùy chỉnh
Bạn có thể chọn điểm đánh dấu kết thúc cho `cat` bằng `<<` như được hiển thị trong ví dụ dưới đây. 
```
[root@Centos7 ~]# cat > muahe.txt <<stop
> Ngay 12/5/2022 co mua to kem theo sam chop
> Sap duoc di quan su
> stop
[root@Centos7 ~]# cat muahe.txt
Ngay 12/5/2022 co mua to kem theo sam chop
Sap duoc di quan su
```

##### 3.4. Sao chép các tập tin
Trong ví dụ thứ ba, bạn sẽ thấy rằng con mèo có thể được sử dụng để sao chép tệp. Chúng tôi sẽ giải thích chi tiết điều gì xảy ra ở đây trong chương bash shell.
```
[root@Centos7 ~]# cat muahe.txt > test1.txt
[root@Centos7 ~]# ls
all  anaconda-ks.cfg  laiduy  muahe.txt  test1.txt  test6.png  test7.png  test8.png  txt.txt
[root@Centos7 ~]# cat test1.txt
Ngay 12/5/2022 co mua
Sap duoc di quan su
```

#### 4. tac
Chỉ một ví dụ sẽ cho bạn thấy mục đích của `tac` (cat quay ngược).
```
[root@Centos7 ~]# cat test1.txt
Ngay 12/5/2022 co mua
Sap duoc di quan su
Di tu ngay 23 - 31/5
[root@Centos7 ~]# tac test1.txt
Di tu ngay 23 - 31/5
Sap duoc di quan su
Ngay 12/5/2022 co mua
```

#### 5. more và less
Lệnh `more` hữu ích để hiển thị các tệp chiếm nhiều màn hình. Hơn sẽ cho phép bạn xem nội dung của từng trang tệp. Sử dụng phím cách để xem tiếp theo hoặc `q` để thoát. Một số người thích lệnh `less` nhiều hơn `more`.

#### 6. strings
Với lệnh `string`, bạn có thể hiển thị các chuỗi `ascii` có thể đọc được tìm thấy trong các tệp (nhị phân).
Ví dụ này xác định vị trí nhị phân `ls` sau đó hiển thị các chuỗi có thể đọc được trong tệp nhị phân (đầu ra bị cắt ngắn).
```
[root@Centos7 ~]# which ls
alias ls='ls --color=auto'
        /usr/bin/ls
[root@Centos7 ~]# strings /usr/bin/ls
/lib64/ld-linux-x86-64.so.2
libselinux.so.1
__gmon_start__
_init
fgetfilecon
freecon
lgetfilecon
_fini
libcap.so.2
cap_to_text
cap_free
cap_get_file
libacl.so.1
acl_get_entry
acl_get_tag_type
acl_extended_file
libc.so.6
...
```

### IV. Cây tệp Linux
Chương này xem xét các thư mục phổ biến nhất trong cây tệp Linux. Nó cũng cho thấy rằng trên Unix mọi thứ đều là một tệp.

#### 1. Thư mục gốc /
Tất cả các hệ thống Linux đều có cấu trúc thư mục bắt đầu từ thư mục gốc. Gốc thư mục được biểu diễn bằng một dấu gạch chéo, như sau: `/`. Mọi thứ tồn tại trên Linux của bạn hệ thống có thể được tìm thấy bên dưới thư mục gốc này. Hãy cùng xem qua nội dung của thư mục gốc.
```
[root@Centos7 ~]# ls /
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var  yasuo
```

#### 2. Thư mục nhị phân
##### 2.1. /bin
Thư mục `/bin` chứa các tệp nhị phân để tất cả người dùng sử dụng. Theo FHS the `/bin` thư mục nên chứa `/bin/cat` và `/bin/date` (trong số những thư mục khác).
```
[root@Centos7 ~]# ls /bin
[                                   fold                   lsattr                pchrt                     sync
ab                                  free                   lsblk                 pflags                    systemctl
addr2line                           gapplication           lscpu                 pgawk                     systemd-analyze
alias                               gawk                   lsinitrd              pgrep                     systemd-ask-password
apropos                             gdbus                  lsipc                 pic                       systemd-cat
ar                                  gencat                 lslocks               pinentry                  systemd-cgls
arch                                genl-ctrl-list         lslogins              pinentry-curses           systemd-cgtop
as                                  geqn                   lsmem                 ping                      systemd-coredumpctl
aserver                             getconf                lsns                  ping6                     systemd-delta
aulast                              getent                 lsscsi                pinky                     systemd-detect-virt
...
```

##### 2.2. /sbin
`/sbin` chứa các tệp nhị phân để cấu hình hệ điều hành. Nhiều mã nhị phân hệ thống yêu cầu `quyền root` để thực hiện các tác vụ nhất định.
Bên dưới ảnh chụp màn hình có chứa mã nhị phân hệ thống để thay đổi địa chỉ ip, phân vùng đĩa và tạo một hệ thống tệp `ext4`.
```
[root@Centos7 ~]#  ls -l /sbin/fdisk /sbin/mkfs.ext4
-rwxr-xr-x. 1 root root 200496 Oct  1  2020 /sbin/fdisk
-rwxr-xr-x. 4 root root  96336 Sep 30  2020 /sbin/mkfs.ext4
```

##### 2.3. /lib
Các mã được tìm thấy trong `/bin` và `/sbin` thường sử dụng các thư viện được chia sẻ nằm trong `/lib`. Dưới đây là một phần nội dung của `/lib`.
```
[root@Centos7 sbin]# ls /lib
binfmt.d  firewalld  grub   kernel      modules         os-release  rpm               sse2      tmpfiles.d  yum-plugins
debug     firmware   kbd    locale      modules-load.d  polkit-1    sendmail          sysctl.d  tuned
dracut    games      kdump  modprobe.d  NetworkManager  python2.7   sendmail.postfix  systemd   udev
```

##### 2.4. /opt
Mục đích của `/opt` là lưu trữ phần mềm tùy chọn. Trong nhiều trường hợp, đây là phần mềm từ bên ngoài kho lưu trữ phân phối. Bạn có thể tìm thấy một thư mục `/opt` trống trên nhiều hệ thống.
Một gói lớn có thể cài đặt tất cả các tệp của nó trong các thư mục con `/bin, /lib, /etc` trong `/opt/$ packagename/`. Ví dụ: nếu gói được gọi là wp, thì nó sẽ cài đặt trong `/opt/wp`, đặt nhị phân trong `/opt/wp/bin` và manpages trong `/opt/wp/man`.

#### 3. Trực tiếp cấu hình
##### 3.1. /boot
Thư mục `/boot` chứa tất cả các tệp cần thiết để khởi động máy tính. Các tệp này không thay đổi rất thường xuyên. Trên các hệ thống Linux, bạn thường tìm thấy thư mục /`boot/grub` tại đây. `/boot/grub` chứa `/boot/grub/grub.cfg` (các hệ thống cũ hơn vẫn có thể có `/boot/grub/grub.conf`) xác định menu khởi động được hiển thị trước khi hạt nhân khởi động.

##### 3.2. /etc
Tất cả các tệp cấu hình dành riêng cho máy phải được đặt trong /etc. Lịch sử `/etc` là viết tắt của `etcetera`, ngày nay mọi người thường sử dụng từ viết tắt của `Editable Text Configuration`. 
Nhiều khi tên của tệp cấu hình giống với ứng dụng, daemon hoặc giao thức với `.conf` được thêm vào làm phần mở rộng.
```
[root@Centos7 ~]#  ls /etc/*.conf
/etc/asound.conf  /etc/host.conf   /etc/ld.so.conf     /etc/locale.conf     /etc/mke2fs.conf    /etc/rsyslog.conf   /etc/sudo-ldap.conf  /etc/yum.conf
/etc/dracut.conf  /etc/kdump.conf  /etc/libaudit.conf  /etc/logrotate.conf  /etc/nsswitch.conf  /etc/sestatus.conf  /etc/sysctl.conf
/etc/e2fsck.conf  /etc/krb5.conf   /etc/libuser.conf   /etc/man_db.conf     /etc/resolv.conf    /etc/sudo.conf      /etc/vconsole.conf
```
Còn nhiều thứ khác được tìm thấy trong `/etc`.
- **/etc/init.d/**
Rất nhiều bản phân phối Unix/Linux có thư mục `/etc/init.d` chứa các tập lệnh để khởi động và dừng `daemon`. Thư mục này có thể biến mất khi Linux chuyển sang các hệ thống thay thế cách khởi động tất cả các `daemon` cũ.

- **/etc/X11//**
Màn hình đồ họa (hay còn gọi là `Hệ thống cửa sổ X` hoặc chỉ `X`) được điều khiển bởi phần mềm từ nền tảng `X.org`. Tệp cấu hình cho màn hình đồ họa của bạn là `/etc/X11/xorg.conf`.

- **/etc/skel/**
Thư mục khung xương `/etc/skel` được sao chép vào thư mục chính của người dùng mới được tạo. Nó thường chứa các tệp ẩn như tập lệnh `.bashrc`.

- **/etc/sysconfig/**
Thư mục này, không được đề cập trong FHS, chứa rất nhiều `Red Hat Enterprise` Các tệp cấu hình Linux. Chúng tôi sẽ thảo luận chi tiết hơn về một số trong số chúng. Ví dụ bên dưới là thư mục `/etc/sysconfig` từ RHELv4u4 với mọi thứ đã được cài đặt.
```
[root@Centos7 ~]# ls /etc/sysconfig/
anaconda    console   ebtables-config  htcacheclean  ip6tables-config  kdump   modules     network-scripts  rsyslog    sshd
authconfig  cpupower  firewalld        httpd         iptables-config   kernel  netconsole  rdisc            run-parts  wpa_supplicant
cbq         crond     grub             init          irqbalance        man-db  network     readonly-root    selinux
```

Tệp `/etc/sysconfig/harddisks` chứa một số tham số để điều chỉnh đĩa cứng. Tập tin giải thích chính nó

#### 4. Thư mục dữ liệu
##### 4.1. /home
Người dùng có thể lưu trữ dữ liệu cá nhân hoặc dự án trong `/home`. Nó là phổ biến (nhưng không bắt buộc bởi the fhs) thực hành đặt tên thư mục chính của người dùng sau tên người dùng ở định dạng `/home/$USERNAME`. Ví dụ:
```
[root@Centos7 ~]# ls /home
3k  laiduy
```
Bên cạnh việc cung cấp cho mọi người dùng (hoặc mọi dự án hoặc nhóm) một vị trí để lưu trữ các tệp cá nhân, thư mục chính của người dùng cũng đóng vai trò như một vị trí để lưu trữ hồ sơ người dùng. Một Unix điển hình hồ sơ người dùng chứa nhiều tệp ẩn (tệp có tên tệp bắt đầu bằng dấu chấm). Ẩn tệp của hồ sơ người dùng Unix chứa các cài đặt dành riêng cho người dùng đó.
```
[root@Centos7 ~]# ls -d /home/laiduy/.*
/home/laiduy/.  /home/laiduy/..  /home/laiduy/.bash_logout  /home/laiduy/.bash_profile  /home/laiduy/.bashrc
```

##### 4.2. /root
Trên nhiều hệ thống `/root` là vị trí mặc định cho dữ liệu cá nhân và hồ sơ của người dùng root.
Nếu nó không tồn tại theo mặc định, thì một số quản trị viên sẽ tạo nó.

##### 4.3. /srv
Bạn có thể sử dụng `/srv` cho dữ liệu được cung cấp bởi hệ thống của bạn. FHS cho phép định vị cv,
dữ liệu rsync, ftp và www ở vị trí này. FHS cũng chấp thuận việc đặt tên quản trị trong `/srv`, như `/srv/project55/ftp` và `/srv/sales/www`.
Trên Sun Solaris (hoặc Oracle Solaris)/`xuất khẩu` được sử dụng cho mục đích này.

##### 4.4. /media
Thư mục `/media` phục vụ như một điểm gắn kết cho các thiết bị đa phương tiện di động như CDROM, máy ảnh kỹ thuật số và các thiết bị gắn USB khác nhau. Kể từ `/media` là khá mới trong thế giới Unix, bạn rất có thể gặp phải các hệ thống chạy mà không có thư mục này. Solaris 9 không có nó, Solaris 10 có. Hầu hết các bản phân phối Linux ngày nay đều gắn kết tất cả các media trong `/media`.   

##### 4.5. /mnt
Thư mục `/mnt` phải trống và chỉ được sử dụng cho các điểm gắn kết tạm thời (theo FHS).
Quản trị viên Unix và Linux đã từng tạo nhiều thư mục ở đây, như `/mnt/something/`. Bạn có thể sẽ gặp phải nhiều hệ thống có nhiều hơn một thư mục được tạo và / hoặc được gắn bên trong `/mnt` để được sử dụng cho các hệ thống tệp cục bộ và từ xa khác nhau.

##### 4.6. /tmp
Các ứng dụng và người dùng nên sử dụng `/tmp` để lưu trữ dữ liệu tạm thời khi cần thiết. Dữ liệu được lưu trữ trong `/tmp` có thể sử dụng không gian đĩa hoặc RAM. Cả hai đều được quản lý bởi điều hành hệ thống. Không bao giờ sử dụng `/tmp` để lưu trữ dữ liệu quan trọng hoặc dữ liệu bạn muốn lưu trữ.

#### 5. Trong thư mục bộ nhớ
##### 5.1. /dev
Các tệp thiết bị trong `/dev` có vẻ là các tệp thông thường, nhưng không thực sự nằm trên đĩa cứng. Thư mục `/dev` chứa các tệp vì hạt nhân đang nhận dạng phần cứng.

**Các thiết bị vật lý thông thường**
Phần cứng phổ biến như thiết bị đĩa cứng được biểu diễn bằng các tệp thiết bị trong `/dev`. Bên dưới là các tệp thiết bị SATA trên máy tính xách tay và sau đó là các ổ gắn IDE trên máy tính để bàn. (Ý nghĩa chi tiết của các thiết bị này sẽ được thảo luận sau.)
```
[root@Centos7 ~]#  ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2
```

##### 5.2. /proc cuộc trò chuyện với kernel
`/proc` là một thư mục đặc biệt khác, có vẻ là các tệp thông thường, nhưng không chiếm đĩa khoảng trống. Nó thực sự là một cái nhìn về hạt nhân, hay tốt hơn là cái mà hạt nhân quản lý, và là một phương tiện để tương tác trực tiếp với nó. `/proc` là một hệ thống tập tin proc.
```
[root@Centos7 ~]# mount -t proc
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
```

Khi liệt kê thư mục `/proc`, bạn sẽ thấy nhiều số (trên mọi Unix) và một số các tệp thú vị (trên Linux).
```
[root@Centos7 ~]# ls /proc
1     1508  16    2027  276  302  391  4    47   550  632  8     asound     diskstats    ioports     loadavg  net           stat           version
10    1509  17    2032  278  303  392  400  480  551  655  809   buddyinfo  dma          irq         locks    pagetypeinfo  swaps          vmallocinfo
11    1511  18    21    279  31   393  401  504  552  659  9     bus        driver       kallsyms    mdstat   partitions    sys            vmstat
1242  1512  1816  22    281  32   394  402  510  554  660  95    cgroups    execdomains  kcore       meminfo  sched_debug   sysrq-trigger  zoneinfo
1251  1518  19    23    282  33   395  41   543  555  670  988   cmdline    fb           keys        misc     schedstat     sysvipc
13    1534  1949  24    283  367  396  42   544  558  675  989   consoles   filesystems  key-users   modules  scsi          timer_list
14    1538  2     273   284  368  397  43   545  560  680  991   cpuinfo    fs           kmsg        mounts   self          timer_stats
15    1540  20    274   285  378  398  44   546  6    681  993   crypto     interrupts   kpagecount  mpt      slabinfo      tty
1507  1560  2004  275   30   379  399  45   549  60   7    acpi  devices    iomem        kpageflags  mtrr     softirqs      uptime
```

Hãy điều tra các thuộc tính tệp bên trong `/proc`. Nhìn vào ngày và giờ sẽ hiển thị ngày và giờ hiện tại hiển thị các tệp được cập nhật liên tục (chế độ xem trên hạt nhân).
```
[root@Centos7 ~]# date
Thu May 12 16:52:27 +07 2022
[root@Centos7 ~]# ls -al /proc/cpuinfo
-r--r--r--. 1 root root 0 May 12 16:52 /proc/cpuinfo
```

Hầu hết các tệp trong `/proc` là 0 byte, nhưng chúng chứa dữ liệu - đôi khi rất nhiều dữ liệu. Bạn có thể thấy điều này bằng cách thực thi cat trên các tệp như `/proc/cpuinfo`, chứa thông tin về CPU.
```
[root@Centos7 ~]# file /proc/cpuinfo
/proc/cpuinfo: empty
[root@Centos7 ~]#  cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 61
model name      : Intel(R) Core(TM) i5-5300U CPU @ 2.30GHz
stepping        : 4
microcode       : 0x2f
cpu MHz         : 2294.690
cache size      : 3072 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 20
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon nopl xtopology tsc_reliable nonstop_tsc eagerfpu pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch invpcid_single ssbd ibrs ibpb stibp fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 invpcid rtm rdseed adx smap xsaveopt arat md_clear spec_ctrl intel_stibp flush_l1d arch_capabilities
bogomips        : 4589.38
clflush size    : 64
cache_alignment : 64
address sizes   : 43 bits physical, 48 bits virtual
power management:
```

- **/proc/interrupts**
Trên kiến ​​trúc x86, `/proc/interrupts` hiển thị các ngắt.
```
[root@Centos7 ~]# cat /proc/interrupts
            CPU0
   0:         80   IO-APIC-edge      timer
   1:        215   IO-APIC-edge      i8042
   8:          1   IO-APIC-edge      rtc0
   9:          0   IO-APIC-fasteoi   acpi
  12:        208   IO-APIC-edge      i8042
  14:          0   IO-APIC-edge      ata_piix
  15:      10795   IO-APIC-edge      ata_piix
  16:       9155   IO-APIC-fasteoi   vmwgfx, snd_ens1371
  17:       8114   IO-APIC-fasteoi   ehci_hcd:usb1, ioc0
  18:        149   IO-APIC-fasteoi   uhci_hcd:usb2
  19:      13236   IO-APIC-fasteoi   ens33
  24:          0   PCI-MSI-edge      PCIe PME, pciehp
  25:          0   PCI-MSI-edge      PCIe PME, pciehp
  26:          0   PCI-MSI-edge      PCIe PME, pciehp
  27:          0   PCI-MSI-edge      PCIe PME, pciehp
  28:          0   PCI-MSI-edge      PCIe PME, pciehp
  29:          0   PCI-MSI-edge      PCIe PME, pciehp
  30:          0   PCI-MSI-edge      PCIe PME, pciehp
  31:          0   PCI-MSI-edge      PCIe PME, pciehp
  32:          0   PCI-MSI-edge      PCIe PME, pciehp
  33:          0   PCI-MSI-edge      PCIe PME, pciehp
  34:          0   PCI-MSI-edge      PCIe PME, pciehp
  35:          0   PCI-MSI-edge      PCIe PME, pciehp
  36:          0   PCI-MSI-edge      PCIe PME, pciehp
  37:          0   PCI-MSI-edge      PCIe PME, pciehp
  38:          0   PCI-MSI-edge      PCIe PME, pciehp
  39:          0   PCI-MSI-edge      PCIe PME, pciehp
  40:          0   PCI-MSI-edge      PCIe PME, pciehp
  41:          0   PCI-MSI-edge      PCIe PME, pciehp
  42:          0   PCI-MSI-edge      PCIe PME, pciehp
  43:          0   PCI-MSI-edge      PCIe PME, pciehp
  44:          0   PCI-MSI-edge      PCIe PME, pciehp
  45:          0   PCI-MSI-edge      PCIe PME, pciehp
  46:          0   PCI-MSI-edge      PCIe PME, pciehp
  47:          0   PCI-MSI-edge      PCIe PME, pciehp
  48:          0   PCI-MSI-edge      PCIe PME, pciehp
  49:          0   PCI-MSI-edge      PCIe PME, pciehp
  50:          0   PCI-MSI-edge      PCIe PME, pciehp
  51:          0   PCI-MSI-edge      PCIe PME, pciehp
  52:          0   PCI-MSI-edge      PCIe PME, pciehp
  53:          0   PCI-MSI-edge      PCIe PME, pciehp
  54:          0   PCI-MSI-edge      PCIe PME, pciehp
  55:          0   PCI-MSI-edge      PCIe PME, pciehp
  56:          0   PCI-MSI-edge      vmw_vmci
  57:          0   PCI-MSI-edge      vmw_vmci
 NMI:          0   Non-maskable interrupts
 LOC:     230294   Local timer interrupts
 SPU:          0   Spurious interrupts
 PMI:          0   Performance monitoring interrupts
 IWI:      15531   IRQ work interrupts
 RTR:          0   APIC ICR read retries
 RES:          0   Rescheduling interrupts
 CAL:          0   Function call interrupts
 TLB:          0   TLB shootdowns
 TRM:          0   Thermal event interrupts
 THR:          0   Threshold APIC interrupts
 DFR:          0   Deferred Error APIC interrupts
 MCE:          0   Machine check exceptions
 MCP:         38   Machine check polls
 ERR:          0
 MIS:          0
 PIN:          0   Posted-interrupt notification event
 NPI:          0   Nested posted-interrupt event
 PIW:          0   Posted-interrupt wakeup event
```

- **/proc/kcore**
Bộ nhớ vật lý được biểu diễn bằng `/proc/kcore`. Đừng cố tạo tệp này, thay vào đó hãy sử dụng trình gỡ lỗi. Kích thước của `/proc/kcore` bằng với bộ nhớ vật lý của bạn, cộng thêm bốn byte.
```
[root@Centos7 ~]# ls -lh /proc/kcore
-r--------. 1 root root 128T May 12 16:57 /proc/kcore
```

##### 5.3. /sys Linux 2.6 cắm nóng
`/proc` là một thư mục đặc biệt khác, có vẻ là các tệp thông thường, nhưng không chiếm đĩa khoảng trống. Nó thực sự là một cái nhìn về hạt nhân, hay tốt hơn là cái mà hạt nhân quản lý, và là một phương tiện để tương tác trực tiếp với nó. `/proc` là một hệ thống tập tin proc.
```
[root@Centos7 ~]# mount -t proc
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
```

Khi liệt kê thư mục `/proc`, bạn sẽ thấy nhiều số (trên mọi Unix) và một số các tệp thú vị (trên Linux).
```
[root@Centos7 ~]# ls /proc
1     1508  16    2059  275  30   379  399  45   549  60   7    acpi       devices      iomem       kpageflags  mtrr          softirqs       uptime
10    1509  17    2061  276  302  391  4    47   550  632  8    asound     diskstats    ioports     loadavg     net           stat           version
11    1511  18    2062  278  303  392  400  480  551  655  809  buddyinfo  dma          irq         locks       pagetypeinfo  swaps          vmallocinfo
1242  1512  1816  21    279  31   393  401  504  552  659  9    bus        driver       kallsyms    mdstat      partitions    sys            vmstat
1251  1518  19    22    281  32   394  402  510  554  660  95   cgroups    execdomains  kcore       meminfo     sched_debug   sysrq-trigger  zoneinfo
13    1534  2     23    282  33   395  41   543  555  670  988  cmdline    fb           keys        misc        schedstat     sysvipc
14    1538  20    24    283  367  396  42   544  558  675  989  consoles   filesystems  key-users   modules     scsi          timer_list
15    1540  2004  273   284  368  397  43   545  560  680  991  cpuinfo    fs           kmsg        mounts      self          timer_stats
1507  1560  2035  274   285  378  398  44   546  6    681  993  crypto     interrupts   kpagecount  mpt         slabinfo      tty
```

#### 6. usr Tài nguyên hệ thống Unix
Mặc dù `/usr` được phát âm giống như người dùng, hãy nhớ rằng nó là viết tắt của `Unix System Resources`. Phân cấp `/usr` phải chứa dữ liệu chỉ đọc, có thể chia sẻ. Một số người chọn để gắn kết `/usr` ở dạng chỉ đọc. Điều này có thể được thực hiện từ phân vùng riêng của nó hoặc từ một chia sẻ NFS chỉ đọc (NFS sẽ được thảo luận ở phần sau).

##### 6.1. /usr/bin
Thư mục `/usr/bin` chứa rất nhiều lệnh.
```
[root@Centos7 ~]# ls /usr/bin | wc -l
672
```

##### 6.2. /usr/include
Thư mục `/usr/include` chứa các tệp tin dùng chung cho C.`
```
[root@Centos7 ~]# ls /usr/include/
python2.7
```

##### 6.3. /usr/lib
Thư mục `/usr/lib` chứa các thư viện không được thực thi trực tiếp bởi người dùng hoặc tập lệnh.
```
[root@Centos7 ~]# ls /usr/lib | head -7
binfmt.d
debug
dracut
firewalld
firmware
games
grub
```

Thư mục /usr/share chứa dữ liệu độc lập về kiến ​​trúc. Như bạn có thể thấy, đây là một thư mục khá lớn.
```
[root@Centos7 ~]# ls /usr/share | wc -l
76
[root@Centos7 ~]# du -sh /usr/share/
213M    /usr/share/
```

Thư mục này thường chứa /usr/share/man cho các trang thủ công.
```
[root@Centos7 ~]# ls /usr/share/man
cs  de  fr  id  ja  man0p  man1p  man2   man3   man3x  man4x  man5x  man6x  man7x  man8x  man9x  nl  pt_BR  sk  tr     zh_TW
da  es  hu  it  ko  man1   man1x  man2x  man3p  man4   man5   man6   man7   man8   man9   mann   pl  ru     sv  zh_CN
```

##### 6.4. /usr/src
Thư mục `/usr/src` là vị trí được khuyến nghị cho các tệp nguồn hạt nhân.
```
[root@Centos7 ~]# ls -l /usr/src/
total 0
drwxr-xr-x. 2 root root 6 Apr 11  2018 debug
drwxr-xr-x. 2 root root 6 Apr 11  2018 kernels
```

#### 7. /var dữ liệu biến
Các tệp có kích thước không thể đoán trước, chẳng hạn như tệp nhật ký, bộ nhớ cache và tệp cuộn, phải được đặt trong `/var`.
##### 7.1. /var/log
Thư mục `/var/log` đóng vai trò là điểm trung tâm để chứa tất cả các tệp nhật ký.
```
[root@Centos7 ~]#  ls /var/log
anaconda  boot.log  cron   dmesg.old  grubby_prune_debug  lastlog  messages  secure   tallylog  wtmp
audit     btmp      dmesg  firewalld  httpd               maillog  rhsm      spooler  tuned     yum.log
```

##### 7.2. /var/log/messages
Tệp đầu tiên điển hình cần kiểm tra khi khắc phục sự cố trên Red Hat (và các dẫn xuất) là `/var/log/syslog`. Theo mặc định, tệp này sẽ chứa thông tin về những gì vừa xảy ra với hệ thống. Tệp được gọi là `/var/log/syslog` trên Debian và Ubuntu.
```
[root@Centos7 ~]# tail /var/log/messages
May 12 17:09:11 Centos7 NetworkManager[681]: <info>  [1652350151.8954] dhcp4 (ens33):   nameserver '192.168.20.2'
May 12 17:09:11 Centos7 NetworkManager[681]: <info>  [1652350151.8954] dhcp4 (ens33):   domain name 'localdomain'
May 12 17:09:11 Centos7 NetworkManager[681]: <info>  [1652350151.8954] dhcp4 (ens33): state changed bound -> bound
May 12 17:09:11 Centos7 dbus[660]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
May 12 17:09:11 Centos7 systemd: Starting Network Manager Script Dispatcher Service...
May 12 17:09:11 Centos7 dhclient[809]: bound to 192.168.20.128 -- renewal in 772 seconds.
May 12 17:09:11 Centos7 dbus[660]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 12 17:09:11 Centos7 systemd: Started Network Manager Script Dispatcher Service.
May 12 17:09:11 Centos7 nm-dispatcher: req:1 'dhcp4-change' [ens33]: new request (2 scripts)
May 12 17:09:11 Centos7 nm-dispatcher: req:1 'dhcp4-change' [ens33]: start running ordered scripts...
```

##### 7.3. /var/cache
Thư mục `/var/cache` có thể chứa dữ liệu bộ nhớ cache cho một số ứng dụng.
```
[root@Centos7 ~]# ls /var/cache
httpd  ldconfig  man  yum
```

##### 7.4. /var/spool
Thư mục `/var/spool` thường chứa các thư mục spool cho mail và cron, nhưng cũng có phục vụ như một thư mục mẹ cho các tệp ống đệm khác.
```
[root@Centos7 ~]# ls /var/spool
anacron  cron  lpd  mail  plymouth  postfix
```

##### 7.5. var/lib
Thư mục `/var/lib` chứa thông tin trạng thái ứng dụng.
Ví dụ: Red Hat Enterprise Linux giữ các tệp liên quan đến rpm trong `/var/lib/rpm/`.
```
[root@Centos7 ~]# ls /var/lib
alternatives  dav   dhclient  initramfs  machines  NetworkManager  plymouth  postfix  rpm-state  stateless  tuned
authconfig    dbus  games     logrotate  misc      os-prober       polkit-1  rpm      rsyslog    systemd    yum
```
### V. Shell expansion
#### 1. Lệnh và tranh luận
Chương này giới thiệu cho bạn cách mở rộng trình bao bằng cách xem kỹ các lệnh và tranh luận. Biết mở rộng shell là rất quan trọng vì nhiều lệnh trên
Hệ thống Linux được xử lý và rất có thể bị thay đổi bởi shell trước khi chúng được thực thi.

Giao diện dòng lệnh hoặc trình bao được sử dụng trên hầu hết các hệ thống Linux được gọi là bash, là viết tắt của Bourne lại shell. Vỏ bash kết hợp các tính năng từ `sh` (bản gốc Bourne shell), `csh` (C Shell) và `ksh` (Korn Shell).

Chương này thường sử dụng lệnh `echo` để chứng minh các tính năng của shell. Lệnh `echo` rất đơn giản: nó lặp lại đầu vào mà nó nhận được.
```
[root@Centos7 ~]# echo LaiKhanhDuy
LaiKhanhDuy
```

##### 1.1. Tranh luận
Một trong những tính năng chính của `shell` là thực hiện quét dòng lệnh. Khi bạn nhập một lệnh tại dấu nhắc lệnh của trình bao và nhấn phím enter, sau đó trình bao sẽ bắt đầu quét dòng đó, cắt nó thành các đối số. Trong khi quét dòng, shell có thể làm nhiều thay đổi đối với các đối số bạn đã nhập. Quá trình này được gọi là `shell expansion`. Khi trình bao hoàn tất quá trình quét và sửa đổi dòng đó, sau đó nó sẽ được thực thi.

##### 1.2. Loại bỏ khoảng trắng
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

##### 1.3. Dấu nháy đơn
Bạn có thể ngăn chặn việc xóa các khoảng trắng bằng cách trích dẫn các khoảng trắng. Nội dung của chuỗi trích dẫn được coi là một đối số. Trong ảnh chụp màn hình bên dưới `echo` nhận được chỉ một đối số.
```
[root@Centos7 ~]# echo 'Lai Duy'
Lai Duy
[root@Centos7 ~]# echo 'Lai      Duy'
Lai      Duy
[root@Centos7 ~]# echo 'Lai            Duy'
Lai            Duy
```

##### 1.4. Dấu ngoặc kép
Bạn cũng có thể ngăn chặn việc xóa các khoảng trắng bằng cách trích dẫn kép các khoảng trắng. Giống như ở trên, `echo` chỉ nhận một đối số.
```
[root@Centos7 ~]# echo "Lai            Duy"
Lai            Duy
```

##### 1.5. echo và trích dẫn
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

#### 2. Lệnh
##### 2.1. type
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

##### 2.2. Chạy các lệnh bên ngoài
Một số lệnh có cả phiên bản nội trang và phiên bản bên ngoài. Khi một trong các lệnh này được thực thi, phiên bản nội trang được ưu tiên. Để chạy phiên bản bên ngoài, bạn phải nhập đường dẫn đầy đủ đến lệnh.
```
[root@Centos7 ~]# type -a echo
echo is a shell builtin
echo is /usr/bin/echo
[root@Centos7 ~]# /bin/echo Running the external echo command...
Running the external echo command...
```

##### 2.3. which
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

#### 3. Bí danh
##### 3.1. Tạo các bí danh
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

##### 3.2. Viết tắt các lệnh
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

##### 3.3. Tùy chọn mặc định
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

##### 3.4. Xem bí danh
Bạn có thể cung cấp một hoặc nhiều bí danh làm đối số cho lệnh bí danh để lấy định nghĩa. Không cung cấp đối số sẽ cung cấp danh sách đầy đủ các bí danh hiện tại.
```
[root@Centos7 ~]# alias . l c
alias .='ls -l'
alias l='.'
alias c='clear'
```

##### 3.5. Bỏ bí danh
Bạn có thể hoàn tác một `alias` bằng lệnh `unalias`.
```
[root@Centos7 ~]# which rm
alias rm='rm -i'
        /usr/bin/rm
[root@Centos7 ~]# unalias rm
[root@Centos7 ~]# which rm
/usr/bin/rm
```

#### 4. Hiển thị shell expansion
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

### VI. Người điều khiển
Trong chương này, chúng tôi đặt nhiều hơn một lệnh trên dòng lệnh bằng cách sử dụng điều khiển các toán tử. Chúng tôi cũng thảo luận ngắn gọn về các tham số liên quan ($?) Và các ký tự đặc biệt tương tự (&).
#### 1. Dấu chấm phẩy (;)
Bạn có thể đặt hai hoặc nhiều lệnh trên cùng một dòng được phân tách bằng dấu chấm phẩy`;` . Cái vỏ sẽ quét dòng cho đến khi nó chạm đến dấu chấm phẩy. Tất cả các đối số trước dấu chấm phẩy này sẽ được coi là một lệnh riêng biệt với tất cả các đối số sau dấu chấm phẩy. Cả hai chuỗi sẽ được thực hiện tuần tự với trình bao chờ mỗi lệnh kết thúc trước đó bắt đầu cái tiếp theo.
```
[root@Centos7 ~]# echo Lai Khanh Duy; echo Sinh nam 2002
Lai Khanh Duy
Sinh nam 2002
```

#### 2. Dấu và (&)
Khi một dòng kết thúc bằng ký hiệu và `&`, shell sẽ không đợi lệnh kết thúc.
Bạn sẽ nhận được lời nhắc trình bao của mình trở lại và lệnh được thực thi ở chế độ nền. Bạn sẽ nhận được thông báo khi lệnh này đã hoàn tất thực thi ở chế độ nền.
```
[root@Centos7 ~]# cd /var 20 &
[1] 1970
[root@Centos7 ~]# cd /var
[1]+  Done                    cd /var 20  (wd: ~)
(wd now: /var)
```

#### 3. Dấu chấm hỏi, đô la ($?)
Mã thoát của lệnh trước đó được lưu trữ trong biến shell `$?`. Trên thực tế `$?` là một tham số shell và không phải là một biến, vì bạn không thể gán giá trị cho `$?`.
```
[root@Centos7 ~]# touch file1
[root@Centos7 ~]# echo $?
0
[root@Centos7 ~]# rm file1
[root@Centos7 ~]# echo $?
0
[root@Centos7 ~]# rm file1
rm: cannot remove ‘file1’: No such file or directory
[root@Centos7 ~]# echo $?
1
```

#### 4. Dấu kép và (&&)
Shell sẽ diễn giải `&&` là `AND logic`. Khi sử dụng `&&`, lệnh thứ hai chỉ được thực thi nếu cái đầu tiên thành công (trả về trạng thái thoát 0).
```
[root@Centos7 ~]# echo Khanh && zcho Duy
Khanh
-bash: zcho: command not found
[root@Centos7 ~]# echo Khanh && echo Duy
Khanh
Duy
[root@Centos7 ~]# acho Khanh && echo Duy
-bash: acho: command not found
[root@Centos7 ~]# echo Khanh && efcho Duy && echo Lai
Khanh
-bash: efcho: command not found
```

Một ví dụ khác về nguyên tắc `logic AND` tương tự. Ví dụ này bắt đầu với một `cd` đang hoạt động theo sau là `ls`, sau đó là cd không hoạt động mà không theo sau là `ls`.
```
[root@Centos7 ~]# cd laiduy && ls
file1  file1.1  file2  file3  test4.txt  test5.txt  test6.txt  Test.txt
[root@Centos7 laiduy]# cd laiduy && ls
-bash: cd: laiduy: No such file or directory
```

#### 5. Thanh dọc kép (||)
`||` đại diện cho một `OR logic`. Lệnh thứ hai chỉ được thực thi khi lệnh đầu tiên lệnh không thành công (trả về trạng thái thoát khác 0).
```
[root@Centos7 ~]# echo Lai || echo Khanh; echo Duy
Lai
Duy
[root@Centos7 ~]# dcho Lai || echo Khanh; echo Duy
-bash: dcho: command not found
Khanh
Duy
```

#### 6. kết hợp && và ||
Bạn có thể sử dụng `logic AND` và `logic OR` này để viết cấu trúc `if-then-else` trên dòng lệnh. Ví dụ này sử dụng `echo` để hiển thị xem lệnh `rm` có thành công hay không.
```
[root@Centos7 ~]# rm test7.png && echo Da xoa || echo Khong tim thay file can xoa
Da xoa
[root@Centos7 ~]# rm test7.png && echo Da xoa || echo Khong tim thay file can xoa
rm: cannot remove ‘test7.png’: No such file or directory
Khong tim thay file can xoa
```

#### 7. Dấu thăng
Mọi thứ được viết sau dấu thăng `(#)` đều bị `shell` bỏ qua. Điều này rất hữu ích để viết một `comment shell`, nhưng không ảnh hưởng đến việc thực thi lệnh hoặc mở rộng shell.
```
[root@Centos7 ~]# mkdir test_# # tao mot thu muc de thu cu phap
[root@Centos7 ~]# ls
all  anaconda-ks.cfg  laiduy  muahe.txt  test_#  test8.png
[root@Centos7 ~]# cd test_#/ # truy cap vao thu muc vua tao
```

#### 7. Thoát các ký tự đặc biệt
Ký tự dấu gạch chéo ngược `\` cho phép sử dụng các ký tự điều khiển, nhưng không có `shell` giải thích nó, điều này được gọi là `ký tự thoát`.
```
[root@Centos7 ~]# echo \Duy \;\Khanh
Duy ;Khanh
[root@Centos7 ~]# echo \Duy \;    \Khanh
Duy ; Khanh
```

#### 8. Dấu gạch chéo ngược cuối dòng
Các dòng kết thúc bằng dấu gạch chéo ngược được tiếp tục ở dòng tiếp theo. `shell` không giải thích ký tự dòng mới và sẽ đợi khi mở rộng trình bao và thực thi dòng lệnh cho đến khi gặp phải một dòng mới không có dấu gạch chéo ngược.
```
[root@Centos7 ~]# echo dau gach cheo \
> aka \
> bka
dau gach cheo aka bka
```












































































































