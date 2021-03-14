---
layout: default
title: CTFd Install
parent: CTFd
nav_order: 1
permalink: /docs/CTFd/CTFd-install
description: "CTFd Install"
---

# CTFd Install
{: .no_toc }


여러 운영체제에서 8080포트로 CTFd Templates 구축
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

+ ## CTFd Template Link

  + [CTFd Github](https://github.com/CTFd/CTFd)
  + [CTFd Live Demo](https://demo.ctfd.io/)
  + [CTFd Site](https://ctfd.io/)
  + [CTFd blog](https://blog.ctfd.io/)
  + [CTFd Documentation](https://docs.ctfd.io/)

<br>

+ ## Ubuntu CTFd Templates Install

  ```bash
  apt update
  # 사용 가능한 패키기와 버전에 대한 리스트 업데이트
  apt upgrade -y
  # 현재 설치되어있는 패키지 최신 버전으로 업그레이드
  ```
  _만약 초기 상태이거나 apt가 최신 버전이 아닌경우 실행_

  우분투 운영체제에 CTFd를 다운받기 위해서는
  먼저 git clone 명령어를 이용하여 github에 있는 CTFd를 다운받고

  ```bash
  git clone https://github.com/CTFd/CTFd.git
  cd CTFd
  vim serve.py
  ```

  vim 편집기를 이용하여 serve.py 파일을 열어보면

  ``parser.add_argument("--port", help="Port for debug server to listen on", default=4000)``
  
  4번줄에 위의 코드가 나오는데
  CTFd를 실행할 포트를 변경하기 위해<본인이 원하는 포트로 변경> 우측에 있는 ``default=4000`` 을 ``default=8080`` 으로 변경한 다음
  
  ``ESC -> :wq -> Enter`` 하면 저장하고 vim 편집기에 빠져나오게 된다.

  



+ ## Red Hat Enterprise Linux CTFd Templates Install
+ ## Windows 10 CTFd Templates Install
+ ## AWS EC2 instance CTFd Templates Install