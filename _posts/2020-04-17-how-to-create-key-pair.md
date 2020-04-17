---
title: "key pair 생성하기"
categories:
  - guide
tags:
  - education
---

## ssh-keygen 명령어를 사용하여 key pair 생성

``` sh
ssh-keygen -t rsa -b 2048 -N "" -C "JH's secret" -f ./my-key-pair.pem
#=> my-key-pair.pem (프라이빗), my-key-pair.pem.pub (퍼블릭) 2개의 키 파일을 쌍으로 생성합니다.
```


## Windows에서 PuTTygen을 사용하여 key pair 생성

[PuTTy 홈페이지][putty-homepage]에서 puttygen을 다운받아 실행합니다.

![스크린샷1](/assets/screenshots/2020-04-17/screenshot1.png)

Paremeters 는 기본 설정 그대로 나둡니다. (Type: RSA, Number of bits: 2048)

Generate 버튼을 클릭합니다. (난수 생성을 위해 마우스를 움직여줘야 합니다.)

![스크린샷2](/assets/screenshots/2020-04-17/screenshot2.png)

Key Comment 는 본인이 원하는 데로 입력하세요.
Key passphrase 는 공란으로 나둡니다.

상단의 Public key 텍스트 영역을 복사하여 파일 이름 "my-key-pair.pem.pub" 으로 저장합니다.  
이 파일이 퍼블릭 키파일 입니다.

![스크린샷3](/assets/screenshots/2020-04-17/screenshot3.png)

상단 메뉴에서 Conversions > Export OpenSSH key 메뉴를 클릭하여 파일 이름 "my-key-pair.pem" 으로 저장합니다.  
이 파일이 프라이빗 키파일 입니다.

![스크린샷4](/assets/screenshots/2020-04-17/screenshot4.png)

### 추가: PPK (PuTTy Private Key) 생성

화면 중간에서 Action > Save private key 버튼을 클릭하여 파일 이름 "my-key-pair.ppk" 으로 저장합니다.
이 파일은 PuTTy 에서만 사용하는 프라이빗 키 파일 포맷이며,
Windows PuTTy 어플리케이션에서 SSH 접속시 사용합니다.
(PEM 프라이빗 키를 사용해서 변환할 수도 있습니다. )

[putty-homepage]: https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
