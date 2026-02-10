### cron 작업계정의 인증만료 확인
- for user in $(sudo ls /var/spool/cron/crontabs/ 2>/dev/null); do     echo "=== $user ===";     sudo chage -l $user;     echo ""; done
~~~
$ for user in $(sudo ls /var/spool/cron/crontabs/ 2>/dev/null); do
>     echo "=== $user ===";
>     sudo chage -l $user;
>     echo "";
> done
=== a ===
마지막으로 암호를 바꾼 날                                       : 12월 31, 2025
암호 만료                               :  3월 31, 2026
암호가 비활성화 기간                                    : 안함
계정 만료                                       : 안함
암호를 바꿀 수 있는 최소 날 수          : 0
암호를 바꿔야 하는 최대 날 수           : 90
암호 만료 예고를 하는 날 수             : 7

=== b ===
마지막으로 암호를 바꾼 날                                       :  2월 10, 2026
암호 만료                               :  5월 11, 2026
암호가 비활성화 기간                                    : 안함
계정 만료                                       : 안함
암호를 바꿀 수 있는 최소 날 수          : 0
암호를 바꿔야 하는 최대 날 수           : 90
암호 만료 예고를 하는 날 수             : 7

=== c ===
마지막으로 암호를 바꾼 날                                       :  2월 10, 2026
암호 만료                               :  5월 11, 2026
암호가 비활성화 기간                                    : 안함
계정 만료                                       : 안함
암호를 바꿀 수 있는 최소 날 수          : 0
암호를 바꿔야 하는 최대 날 수           : 90
암호 만료 예고를 하는 날 수             : 7
~~~
### cron 작업(계정) 확인
~~~
$ sudo ls -la /var/spool/cron/crontabs/
합계 20
drwx-wx--T 2 root  crontab 4096  2월 10 19:20 .
drwxr-xr-x 3 root  root    4096  7월 20  2016 ..
-rw------- 1 a crontab 1455  6월 12  2024 a
-rw------- 1 b crontab 1602  2월 10 19:20 b
-rw------- 1 c crontab 1557  2월 10 18:32 c
~~~
