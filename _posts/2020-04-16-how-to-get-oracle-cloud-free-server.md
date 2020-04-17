---
title: "오라클 클라우드 무료 개발 서버"
categories:
  - guide
tags:
  - education
---

오라클 클라우드(OCI)는 기간 제한 없는 무료 서비스를 제공하고 있어
~~비록 저사양이긴 하지만~~ 비용적인 부담 없이 가상 서버(VM)를 운영할 수 있습니다.

바로 VM 서버를 생성해 보겠습니다.

먼저 [Oracle Cloud Free Tier 소개 페이지][oracle-cloud-free] 에서 회원 가입을 해 주세요

- 회원 가입 시 Country 와 Home Region 를  South Korea 로 선택하세요.
- 모바일 SMS 인증시 휴대전화 번호의 맨 앞자리 0을 제외하고 입력해 주세요.  
  예) 010xxxxyyyy => 10xxxxyyyy
- 카드 인증시 Billing Address 를 체크합니다. 카드사에 등록된 주소와 국가/우편번호 등이 일치하는 지 확인해 주세요.
{: .notice--danger}

이제 오라클 클라우드 콘솔 화면에 로그인 할 수 있습니다.

![스크린샷1](/assets/screenshots/2020-04-16/screenshot1.png)

VM 인스턴스를 생성하기 전에 먼저 개인 key pair 를 준비해 주세요.

[key pair 생성하기][how-to-create-key-pair]

이제 VM을 생성합니다.
![스크린샷2](/assets/screenshots/2020-04-16/screenshot2.png)
1. 인스턴스 이름을 원하는 이름으로 바꿔주세요. (instance-my-vm1)
2. 원하는 이미지 소스를 선택합니다.   
  (CentOS, Ubuntu가 무난합니다.
  저는 Ubuntu 18.04 Minimal 을 선택 했습니다.)
3. [구성, 네트워크 및 스토리지 옵션 표시] 를 클릭하여,네트워킹 이름을 원하는 이름으로 바꿔주세요 (vcn-my-network)
4. [SSH 키 추가]에서 앞서 생성한 key pair 의 퍼블릭 키 파일을 선택하세요 (my-key-pair.pem.pub) 

5. 생성 버튼을 클릭합니다.

   2020-04-16 현재 아래와 같이 VM 생성이 실패하고 있습니다.
   ![스크린샷3](/assets/screenshots/2020-04-16/screenshot3.png)
   현재 OCI 센터의 FreeTier 가용량이 부족하기 때문입니다. 
   나중에 다시 합시다.
   {: .notice--danger}


[oracle-cloud-free]: https://www.oracle.com/kr/cloud/free/
[how-to-create-key-pair]: ({% post_url 2020-04-17-how-to-create-key-pair %})

[Some Link]