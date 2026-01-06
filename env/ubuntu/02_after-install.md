### SSH 포트변경 및 재시작
~~~
:/etc/ssh$vi sshd_config
...
Port 764
...
$ sudo ss -tulpn | grep ssh
tcp   LISTEN 0      4096         0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=2510,fd=3),("systemd",pid=1,fd=65))
tcp   LISTEN 0      4096            [::]:22           [::]:*    users:(("sshd",pid=2510,fd=4),("systemd",pid=1,fd=67))
:/etc/ssh$ sudo systemctl disable --now ssh.socket
Removed "/etc/systemd/system/sockets.target.wants/ssh.socket".
Removed "/etc/systemd/system/ssh.service.requires/ssh.socket".
:/etc/ssh$ sudo systemctl disable --now ssh.socket && sudo systemctl restart ssh
:/etc/ssh$ sudo ss -tulpn | grep ssh
tcp   LISTEN 0      128          0.0.0.0:764       0.0.0.0:*    users:(("sshd",pid=2996,fd=3))
tcp   LISTEN 0      128             [::]:764          [::]:*    users:(("sshd",pid=2996,fd=4))
~~~
