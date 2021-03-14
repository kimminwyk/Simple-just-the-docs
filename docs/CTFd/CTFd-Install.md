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

+ ## AWS EC2 instance CTFd Templates Install

<br>

---

<br>

+ ## Ubuntu CTFd Templates Install

  ```bash
  apt update
  # 사용 가능한 패키기와 버전에 대한 리스트 업데이트
  apt upgrade -y
  # 현재 설치되어있는 패키지 최신 버전으로 업그레이드
  ```

  우분투 운영체제에 CTFd를 다운받기 위해서는
  먼저 git clone 명령어를 이용하여 github에 있는 CTFd를 다운받고

  ```bash
  git clone https://github.com/CTFd/CTFd.git
  # github에 있는 CTFd git 다운로드
  cd CTFd
  vim serve.py
  # 구성 설정을 위해 vim 편집기를 이용하여 serve.py 편집
  ```

  vim 편집기를 이용하여 serve.py 파일을 열어보면

  ``parser.add_argument("--port", help="Port for debug server to listen on", default=4000)``
  
  4번줄에 위의 코드가 나오는데
  CTFd를 실행할 포트를 변경하기 위해<본인이 원하는 포트로 변경> 우측에 있는 ``default=4000`` 을 ``default=8080`` 으로 변경하고 
  하단의 ``app.run(debug=True, threaded=True, host="127.0.0.1", port=args.port)`` 부분의 ``host="127.0.0.1"`` 을 ``host="0.0.0.0"`` 으로 바꾼 다음
  
  ``ESC -> :wq -> Enter`` 저장하고 빠져나온 다음

  만약 python3가 깔려 있지 않은 경우 설치해줘야된다.

  ```bash
  apt install python3 python3-pip -y
  python3 serve.py
  ```

<br>

---

<br>

+ ## Red Hat Enterprise Linux CTFd Templates Install



+ ## Windows 10 CTFd Templates Install



+ ## Docker Ubuntu CTFd Templates Install

  1. apt 업데이트 & 업그레이드
  2. docker package 설치
  3. docker ctfd/ctfd 이미지 설치
  4. docker 컨테이너 생성 또는 실행
  5. docker CTFd 컨테이너 접속
  6. vim 편집기를 이용하여 host 또는 port 변경
  7. serve.py 실행
  8. <public IPv4>:8080 CTFd 접속

  <br>

  ```bash
  apt update
  # 사용 가능한 패키지와 버전에 대한 리스트 업데이트
  apt upgrade -y
  # 현재 설치되어있는 패키지 최신 버전으로 업그레이드
  apt install docker docker.io docker-compose -y
  # docker 관련된 패키지 다운로드
  docker pull ctfd/ctfd
  # docker ctfd/ctfd 이미지 다운로드
  docker run -it -d -p 8080:8080 --name=CTFd ctfd/ctfd
  # docker ctfd/ctfd 이미지로 컨테이너 생성 및 시작
  docker start CTFd
  # docker CTFd 컨테이너 시작
  docker exec -it --user=root CTFd bash
  # 명령어 치기 위해 docker CTFd 컨테이너 접속
  root@docker: apt update
    # 사용 가능한 패키지와 버전에 대한 리스트 업데이트
  root@docker: apt upgrade -y
    # 현재 설치되어있는 패키지 최신 버전으로 업그레이드
  root@docker: apt install vim python3 python3-pip -y
    # CTFd 구축을 위한 python3 python3-pip vim 설치
  root@docker: vim serve.py
    # vim 편집기를 이용하여 serve.py 파일 편집
  ```

  docker 컨테이너 안에서 vim 편집기를 이용하여 serve.py 파일을 연 다음 ``parser.add_argument("--port", help="Port for debug server to listen on", default=4000)``
  
  4번줄에 위의 코드가 나오는데
  CTFd를 실행할 포트를 변경하기 위해\<본인이 원하는 포트로 변경\> 우측에 있는 
  ``default=4000`` 을 ``default=8080`` 으로 변경하고 
  하단의 ``app.run(debug=True, threaded=True, host="127.0.0.1", port=args.port)`` 
  부분의 
  ``host="127.0.0.1"`` 
  -> ``host="0.0.0.0"``
  으로 바꾼 다음
  
  ``ESC -> :wq -> Enter`` 저장하고 빠져나온 다음

  ```bash
  python3 serve.py
  # python3 명령어를 이용하여 serve.py 파일 실행
  ```

  serve.py 파일을 실행한 다음
  <public IPv4>:8080 으로 접속하면
  
  ![CTFd-Setup](/post-images/CTFd/CTFd-install/CTFd-Setup.png)

  이렇게 정상적으로 CTFd구축에 성공한것을 볼 수 있습니다.
