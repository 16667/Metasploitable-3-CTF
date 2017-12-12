## Joker

With a simple command we find the joker flag:

```
root@ip-10-0-101-252:~# find / -name 'joker.png'
/etc/joker.png
```

![Fake Flag](img/img1.png)

Hey, something is wrong here, it seems that colors are messed up, let's invert them with GIMP


![Gimp](img/img2.png)

Then we can save it without any flags in order to not add metadata:

![Gimp](img/img3.png)

We get it:

![Flag](img/img4.png)

`MD5 = 69ac2a39f42e91896b19a123e5e4d2a9`