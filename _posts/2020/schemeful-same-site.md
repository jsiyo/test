---
title: Chrome 업데이트 Schemeful Same-Site을 대응하자.
date: 2021-02-19
tags: [Tech]
excerpt: Schemeful Same-Site
---

**`Same-Site`**의 후속으로 **`Schemeful Same-Site`**에 대한 업데이트 내용이다.  
[Chrome Platform Status](https://chromestatus.com/feature/5096179480133632)에 <U>따르면 Chrome M88</U>부터  
적용될 예정이며 <U>2021년 1월</U> 배포 예정이라고 함.  

## 용어
### - scheme
URL에서 http, https 부분을 **`scheme`**라고 한다.  
ex) <U>https</U>://blog.jaysiyo.com
### - cross-scheme
**`http`**://blog.jaysiyo.com 와 **`https`**://blog.jaysiyo.com는  
다른 **`scheme`**을 사용함으로 두 관계를 **`cross-scheme`**라고 함.

## Schemeful Same-Site
이전에는 같은 도메인의 HTTP 사이트와 HTTPS 사이트를 Same-Site로 취급했다.  
Cookie의 SameSite 속성을 Strict 또는 Lax로 설정하면 사이트 간의 Cookie를 보낼 수 있었음.  

하지만 Schemeful Same-Site가 적용된 후  
HTTP 사이트와 HTTPS 사이트를 cross-site로 취급한다.  
![](../images/to-be.png)

cross-site로 취급하기 때문에 Cookie의 SameSite 속성을  
Strict로 설정시 사이트 간의 Cookie를 보낼 수 없다.  
Lax로 설정한 쿠키도 때에 따라 불가능.
### - Scenarios
- **Navigation**
![](../images/cross-scheme-navigation.png)

> Cross-scheme navigation from HTTP to HTTPS.

|  | HTTP → HTTPS | HTTPS → HTTP |
|---|:---:|:---:|
| SameSite=Strict | ⛔ Blocked | ⛔ Blocked |
| SameSite=Lax | ✔ Allowed | ✔ Allowed |
| SameSite=None;Secure | ✔ Allowed | ⛔ Blocked |

- **POSTing a form**
![](../images/cross-scheme-form-submission.png)

> Cross-scheme form submission from HTTP to HTTPS.

|  | HTTP → HTTPS | HTTPS → HTTP |
|---|:---:|:---:|
| SameSite=Strict | ⛔ Blocked | ⛔ Blocked |
| SameSite=Lax | ⛔ Blocked | ⛔ Blocked |
| SameSite=None;Secure | ✔ Allowed | ⛔ Blocked |

## 결론
HTTPS를 사용하면 문제없음.

## 출처
[https://chromestatus.com/feature/5096179480133632](https://chromestatus.com/feature/5096179480133632)  
[https://web.dev/schemeful-samesite/](https://web.dev/schemeful-samesite/)  
[https://github.com/sbingler/schemeful-same-site](https://github.com/sbingler/schemeful-same-site)  
[https://tech.kakao.com/2021/02/02/frontend-growth-06/](https://tech.kakao.com/2021/02/02/frontend-growth-06/)


