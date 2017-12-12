## 6 of Clubs


Under the /opt folder there is the sinatra binary, lets try to understand what is is:

```
root@ip-10-0-101-252:/opt/sinatra# ps aux  | grep sinatra
root     12783  0.0  0.0   4456   660 ?        S    13:42   0:00 /bin/sh -c cd /opt/sinatra && ruby -e "require 'obfuscate'; Obfuscate.setup { |c| c.salt = 'sinatra'; c.mode = :string }; cr = Obfuscate.clarify(File.read('.raIhUJTLEMAfUW3GmynyFySPw')); File.delete('.raIhUJTLEMAfUW3GmynyFySPw') if File.exists?('.raIhUJTLEMAfUW3GmynyFySPw'); eval(cr)" --
root     12784  0.7  1.1 104280 22604 ?        Sl   13:42   0:02 ruby -e require 'obfuscate'; Obfuscate.setup { |c| c.salt = 'sinatra'; c.mode = :string }; cr = Obfuscate.clarify(File.read('.raIhUJTLEMAfUW3GmynyFySPw')); File.delete('.raIhUJTLEMAfUW3GmynyFySPw') if File.exists?('.raIhUJTLEMAfUW3GmynyFySPw'); eval(cr)
root     12888  0.0  0.0  10476   932 pts/4    S+   13:47   0:00 grep --color=auto sinatra
```

Sinatra is a ruby framework for quick developing, the sinastra executable seems to create the .raIhUJTLEMAfUW3GmynyFySPw file
and serving it in some way. Our research on the web pointed us to this github repository  https://github.com/mguymon/obfuscate,
a ruby obfuscator. Let's try to write a ruby script to deobfuscate the text.

Dec.rb:

```
require 'obfuscate'
Obfuscate.setup do |c| 
c.salt = 'sinatra'
c.mode = :string
end
cr = Obfuscate.clarify(File.read('./backup/img'))
print cr
```

Now let's use the script to get the png:

```
cd /opt/sinatra
mkdir backup
cp .raIhUJTLEMAfUW3GmynyFySPw ./backup/
backup/.raIhUJTLEMAfUW3GmynyFySPw ./backup/img
ruby dec.rb  > ciao.txt
nano ciao.txt 
cat ciao.txt | base64 -d > 6_of_clubs.png
```

![Flag](./img/img1.png)

`MD5  = d9247a49d132a4f92dcc813f63eb1c8`