---
title: 아파치 웹 서버 사용자 인증
date: 2021-02-20
tags: [Tech]
excerpt: htpasswd - basic authentication
---

## Basic Authentication
Apache 웹 서버는 디렉터리에 **`HTTP Basic Authentication`** 을 설정하여 사용자가 해당 디렉터리에 접근했을 때   
간단한 인증 방식을 통하여 접근 제한을 할 수 있다.  
인증 유형은 가장 기본인 <U>Basic</U> 으로 설정하였음.  
> **Basic ([RFC 7617](https://datatracker.ietf.org/doc/html/rfc7617) base64-encoded credentials)**

---

```apache
htpasswd -c /etc/httpd/.htpasswd jaysiyo
New password: 
Re-type new password:
```
> - htpasswd [옵션] [사용자 인증 파일] [사용자명]  
> htpasswd 명령어를 통하여 사용자 인증에 필요한 파일 생성 및 사용자를 추가함.  


```apache
<Directory /var/www/html>
    AuthType Basic
    AuthName "Basic Authentication"
    AuthUserFile /etc/httpd/.htpasswd
    Require valid-user
    #AllowOverride AuthConfig 
</Directory>
```

> - **[&lt;Directory /var/www/html&gt;](https://httpd.apache.org/docs/2.4/ko/mod/core.html#directory)**  
인증을 사용할 디렉터리 경로  
> - **[AuthType](https://httpd.apache.org/docs/2.4/ko/mod/mod_authn_core.html#authtype)**  
인증 유형을 설정함  
Basic ([mod_auth_basic](https://httpd.apache.org/docs/2.4/mod/mod_auth_basic.html)), Digest ([mod_auth_digest](https://httpd.apache.org/docs/2.4/ko/mod/mod_auth_digest.html))  
> - **[AuthName](https://httpd.apache.org/docs/2.4/ko/mod/mod_authn_core.html#authname)**
브라우저에서 제공하는 암호 대화 상자에 표시됨  
> - **[AuthUserFile](https://httpd.apache.org/docs/2.4/ko/mod/mod_authn_file.html#authuserfile)**
사용자 인증을 하기 위해 필요한 정보가 담긴 파일을 지정함  
> - **[Require](https://httpd.apache.org/docs/2.4/ko/mod/mod_authz_core.html#require)**  
인증된 사용자가 설정에 의해 권한이 있는지 확인함  
Require valid-user 인증에 성공한 모든 사용자를 엑세스 허용  
> - [AllowOverride AuthConfig](https://httpd.apache.org/docs/current/ko/mod/core.html#allowoverride)  
.htaccess 파일의 설정으로 적용됨

## 참고
[https://httpd.apache.org/docs/2.4/ko/programs/htpasswd.html](https://httpd.apache.org/docs/2.4/ko/programs/htpasswd.html)  
[https://developer.mozilla.org/ko/docs/Web/HTTP/Authentication](https://developer.mozilla.org/ko/docs/Web/HTTP/Authentication)








