## 9 of Diamonds

We find an iso in te kylo_ren directory:

```
root@ip-10-0-101-252:/home/kylo_ren# ls -lah
total 28K
drwxr-xr-x  4 kylo_ren users 4.0K Nov  7 16:45 .
drwxr-xr-x 19 root     root  4.0K Dec  5 13:28 ..
-rw-r--r--  1 kylo_ren users  220 Apr  9  2014 .bash_logout
-rw-r--r--  1 kylo_ren users 3.6K Apr  9  2014 .bashrc
drwxr-xr-x  3 root     root  4.0K Nov  7 16:42 poc
-rw-r--r--  1 kylo_ren users  675 Apr  9  2014 .profile
drw---x---  2 kylo_ren users 4.0K Nov  7 16:45 .secret_files
root@ip-10-0-101-252:/home/kylo_ren# ls -lah .secret_files/
total 680K
drw---x--- 2 kylo_ren users 4.0K Nov  7 16:45 .
drwxr-xr-x 4 kylo_ren users 4.0K Nov  7 16:45 ..
-rw---x--- 1 kylo_ren users 672K Nov  7 16:45 my_recordings_do_not_open.iso
```

Let's mount it:

```
root@ip-10-0-101-252:/home/kylo_ren/.secret_files# mount -o loop my_recordings_do_not_open.iso /media/
mount: block device /home/kylo_ren/.secret_files/my_recordings_do_not_open.iso is write-protected, mounting read-only
root@ip-10-0-101-252:/home/kylo_ren/.secret_files# ls /media/
9_of_diamonds.png
```

![Flag](img/img1.png)

`MD5  = 097a0b9b4b08580caa5509941d7e548d`
