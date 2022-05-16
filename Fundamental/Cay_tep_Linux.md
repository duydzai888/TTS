# Cây tệp Linux
Chương này xem xét các thư mục phổ biến nhất trong cây tệp Linux. Nó cũng cho thấy rằng trên Unix mọi thứ đều là một tệp.
## 1. Thư mục gốc /
Tất cả các hệ thống Linux đều có cấu trúc thư mục bắt đầu từ thư mục gốc. Gốc thư mục được biểu diễn bằng một dấu gạch chéo, như sau: `/`. Mọi thứ tồn tại trên Linux của bạn hệ thống có thể được tìm thấy bên dưới thư mục gốc này. Hãy cùng xem qua nội dung của thư mục gốc.
```
[root@Centos7 ~]# ls /
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var  yasuo
```

## 2. Thư mục nhị phân
### 2.1. /bin
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
...
```

### 2.2. /sbin
`/sbin` chứa các tệp nhị phân để cấu hình hệ điều hành. Nhiều mã nhị phân hệ thống yêu cầu `quyền root` để thực hiện các tác vụ nhất định.
Bên dưới ảnh chụp màn hình có chứa mã nhị phân hệ thống để thay đổi địa chỉ ip, phân vùng đĩa và tạo một hệ thống tệp `ext4`.
```
[root@Centos7 ~]#  ls -l /sbin/fdisk /sbin/mkfs.ext4
-rwxr-xr-x. 1 root root 200496 Oct  1  2020 /sbin/fdisk
-rwxr-xr-x. 4 root root  96336 Sep 30  2020 /sbin/mkfs.ext4
```

### 2.3. /lib
Các mã được tìm thấy trong `/bin` và `/sbin` thường sử dụng các thư viện được chia sẻ nằm trong `/lib`. Dưới đây là một phần nội dung của `/lib`.
```
[root@Centos7 sbin]# ls /lib
binfmt.d  firewalld  grub   kernel      modules         os-release  rpm               sse2      tmpfiles.d  yum-plugins
debug     firmware   kbd    locale      modules-load.d  polkit-1    sendmail          sysctl.d  tuned
dracut    games      kdump  modprobe.d  NetworkManager  python2.7   sendmail.postfix  systemd   udev
```

### 2.4. /opt
Mục đích của `/opt` là lưu trữ phần mềm tùy chọn. Trong nhiều trường hợp, đây là phần mềm từ bên ngoài kho lưu trữ phân phối. Bạn có thể tìm thấy một thư mục `/opt` trống trên nhiều hệ thống.
Một gói lớn có thể cài đặt tất cả các tệp của nó trong các thư mục con `/bin, /lib, /etc` trong `/opt/$ packagename/`. Ví dụ: nếu gói được gọi là wp, thì nó sẽ cài đặt trong `/opt/wp`, đặt nhị phân trong `/opt/wp/bin` và manpages trong `/opt/wp/man`.

## 3. Trực tiếp cấu hình
### 3.1. /boot
Thư mục `/boot` chứa tất cả các tệp cần thiết để khởi động máy tính. Các tệp này không thay đổi rất thường xuyên. Trên các hệ thống Linux, bạn thường tìm thấy thư mục /`boot/grub` tại đây. `/boot/grub` chứa `/boot/grub/grub.cfg` (các hệ thống cũ hơn vẫn có thể có `/boot/grub/grub.conf`) xác định menu khởi động được hiển thị trước khi hạt nhân khởi động.

### 3.2. /etc
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

## 4. Thư mục dữ liệu
### 4.1. /home
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

### 4.2. /root
Trên nhiều hệ thống `/root` là vị trí mặc định cho dữ liệu cá nhân và hồ sơ của người dùng root.
Nếu nó không tồn tại theo mặc định, thì một số quản trị viên sẽ tạo nó.

### 4.3. /srv
Bạn có thể sử dụng `/srv` cho dữ liệu được cung cấp bởi hệ thống của bạn. FHS cho phép định vị cv,
dữ liệu rsync, ftp và www ở vị trí này. FHS cũng chấp thuận việc đặt tên quản trị trong `/srv`, như `/srv/project55/ftp` và `/srv/sales/www`.
Trên Sun Solaris (hoặc Oracle Solaris)/`xuất khẩu` được sử dụng cho mục đích này.

### 4.4. /media
Thư mục `/media` phục vụ như một điểm gắn kết cho các thiết bị đa phương tiện di động như CDROM, máy ảnh kỹ thuật số và các thiết bị gắn USB khác nhau. Kể từ `/media` là khá mới trong thế giới Unix, bạn rất có thể gặp phải các hệ thống chạy mà không có thư mục này. Solaris 9 không có nó, Solaris 10 có. Hầu hết các bản phân phối Linux ngày nay đều gắn kết tất cả các media trong `/media`.   

### 4.5. /mnt
Thư mục `/mnt` phải trống và chỉ được sử dụng cho các điểm gắn kết tạm thời (theo FHS).
Quản trị viên Unix và Linux đã từng tạo nhiều thư mục ở đây, như `/mnt/something/`. Bạn có thể sẽ gặp phải nhiều hệ thống có nhiều hơn một thư mục được tạo và / hoặc được gắn bên trong `/mnt` để được sử dụng cho các hệ thống tệp cục bộ và từ xa khác nhau.

### 4.6. /tmp
Các ứng dụng và người dùng nên sử dụng `/tmp` để lưu trữ dữ liệu tạm thời khi cần thiết. Dữ liệu được lưu trữ trong `/tmp` có thể sử dụng không gian đĩa hoặc RAM. Cả hai đều được quản lý bởi điều hành hệ thống. Không bao giờ sử dụng `/tmp` để lưu trữ dữ liệu quan trọng hoặc dữ liệu bạn muốn lưu trữ.

## 5. Trong thư mục bộ nhớ
### 5.1. /dev
Các tệp thiết bị trong `/dev` có vẻ là các tệp thông thường, nhưng không thực sự nằm trên đĩa cứng. Thư mục `/dev` chứa các tệp vì hạt nhân đang nhận dạng phần cứng.

**Các thiết bị vật lý thông thường**
Phần cứng phổ biến như thiết bị đĩa cứng được biểu diễn bằng các tệp thiết bị trong `/dev`. Bên dưới là các tệp thiết bị SATA trên máy tính xách tay và sau đó là các ổ gắn IDE trên máy tính để bàn. (Ý nghĩa chi tiết của các thiết bị này sẽ được thảo luận sau.)
```
[root@Centos7 ~]#  ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2
```

### 5.2. /proc cuộc trò chuyện với kernel
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
...
```

- **/proc/kcore**
Bộ nhớ vật lý được biểu diễn bằng `/proc/kcore`. Đừng cố tạo tệp này, thay vào đó hãy sử dụng trình gỡ lỗi. Kích thước của `/proc/kcore` bằng với bộ nhớ vật lý của bạn, cộng thêm bốn byte.
```
[root@Centos7 ~]# ls -lh /proc/kcore
-r--------. 1 root root 128T May 12 16:57 /proc/kcore
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

### 5.3. /sys Linux 2.6 cắm nóng
Thư mục `/sys` được tạo cho nhân Linux 2.6. Kể từ phiên bản 2.6, Linux sử dụng `sysfs` để hỗ trợ các thiết bị cắm nóng USB và IEEE 1394 (FireWire). Xem các trang hướng dẫn sử dụng của udev (8) (kế thừa của devfs) và hotplug (8) 
Về cơ bản thư mục `/sys` chứa thông tin hạt nhân về phần cứng
 type proc (rw,nosuid,nodev,noexec,relatime)

## 6. usr Tài nguyên hệ thống Unix
Mặc dù `/usr` được phát âm giống như người dùng, hãy nhớ rằng nó là viết tắt của `Unix System Resources`. Phân cấp `/usr` phải chứa dữ liệu chỉ đọc, có thể chia sẻ. Một số người chọn để gắn kết `/usr` ở dạng chỉ đọc. Điều này có thể được thực hiện từ phân vùng riêng của nó hoặc từ một chia sẻ NFS chỉ đọc (NFS sẽ được thảo luận ở phần sau).

### 6.1. /usr/bin
Thư mục `/usr/bin` chứa rất nhiều lệnh.
```
[root@Centos7 ~]# ls /usr/bin | wc -l
672
```
### 6.2. /usr/include
Thư mục `/usr/include` chứa các tệp tin dùng chung cho C.`
```
[root@Centos7 ~]# ls /usr/include/
python2.7
```

### 6.3. /usr/lib
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

### 6.4. /usr/src
Thư mục `/usr/src` là vị trí được khuyến nghị cho các tệp nguồn hạt nhân.
```
[root@Centos7 ~]# ls -l /usr/src/
total 0
drwxr-xr-x. 2 root root 6 Apr 11  2018 debug
drwxr-xr-x. 2 root root 6 Apr 11  2018 kernels
```

## 7. /var dữ liệu biến
Các tệp có kích thước không thể đoán trước, chẳng hạn như tệp nhật ký, bộ nhớ cache và tệp cuộn, phải được đặt trong `/var`.
### 7.1. /var/log
Thư mục `/var/log` đóng vai trò là điểm trung tâm để chứa tất cả các tệp nhật ký.
```
[root@Centos7 ~]#  ls /var/log
anaconda  boot.log  cron   dmesg.old  grubby_prune_debug  lastlog  messages  secure   tallylog  wtmp
audit     btmp      dmesg  firewalld  httpd               maillog  rhsm      spooler  tuned     yum.log
```

### 7.2. /var/log/messages
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

### 7.3. /var/cache
Thư mục `/var/cache` có thể chứa dữ liệu bộ nhớ cache cho một số ứng dụng.
```
[root@Centos7 ~]# ls /var/cache
httpd  ldconfig  man  yum
```

### 7.4. /var/spool
Thư mục `/var/spool` thường chứa các thư mục spool cho mail và cron, nhưng cũng có phục vụ như một thư mục mẹ cho các tệp ống đệm khác.
```
[root@Centos7 ~]# ls /var/spool
anacron  cron  lpd  mail  plymouth  postfix
```

### 7.5. var/lib
Thư mục `/var/lib` chứa thông tin trạng thái ứng dụng.
Ví dụ: Red Hat Enterprise Linux giữ các tệp liên quan đến rpm trong `/var/lib/rpm/`.
```
[root@Centos7 ~]# ls /var/lib
alternatives  dav   dhclient  initramfs  machines  NetworkManager  plymouth  postfix  rpm-state  stateless  tuned
authconfig    dbus  games     logrotate  misc      os-prober       polkit-1  rpm      rsyslog    systemd    yum
```