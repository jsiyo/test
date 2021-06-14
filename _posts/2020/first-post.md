---
title: 첫 번째 글
date: 2021-02-18
tags: [Etc]
excerpt: First Posting
---

# Refactoring
오랜만에 블로그 포스팅 하려고 마음을 먹고 작성해서 deploy를 하는 순간 빌드에 문제가 발생하였다..😭  
[**`netlify`**](https://www.netlify.com/)의 deploy log를 확인 후 빌드가 안되는 이유를 찾아보니까  
모듈이 구식이라 손을 좀 봐야 하는 상황인 듯.

이참에 블로그 리팩토링을 결심하고  
요즘 핫한 [**`Jam stack`**](https://jamstack.org/) 방식을 활용하기 위해서 `React` 기반의 [**`gatsby`**](https://www.gatsbyjs.com/)로 선택하였다.  
기존 블로그는 잠시 묻어두고..

그리고 netlify 빌드에 `Total build minutes used` 라는 제한이 생겼다.  
월간 무료 빌드 시간 300분을 제공하고 추가는 Payment method가 있는 거 보니 결제를 해야 하나보다.  
일단은 알고만 있고 패스..

이렇게 첫 번째 포스팅을 작성하게 되었다. 미니멀한게 마음에 쏙 든다.

앞으로 얼마나 꾸준히 할 수 있을지는 모르겠지만  
일단 리팩토링은 성공.🎉

---

```php
<?php
printf('Hello, World!');
```




