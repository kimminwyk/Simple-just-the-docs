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

---

<br>

+ ## AWS EC2 instance CTFd Templates Install

  1. AWS EC2 접속
  2. Amazon Machine Image 선택
  3. 인스턴스 유형 선택
  4. 보안 그룹 구성
  5. 인스턴스 SSH연결을 위한 키페어.pem 생성
  6. PuTTYGen으로 키페어.pem ppk로 변경
  7. PuTTY 실행 후 ppk 파일 추가
  8. PuTTY를 이용하여 AWS EC2 instance 연결

  먼저 AWS 서비스중 EC2를 찾고

  ![AWS CTFd Install](/post_images/CTFd/CTFd-install/AWS-EC2.png)

  AWS EC2 인스턴스 생성할때 사용할 운영체제는 Ubuntu 18.04 LTS버전으로 선택한 다음

  ![AmazonMachineImage](/post_images/CTFd/CTFd-install/AmazonMachineImage.png)

  CTFd를 구축할 인스턴스의 사양을 선택하고

  ![instance Type Select](/post_images/CTFd/CTFd-install/instance-type-select.png)

  CTFd를 구축하면서 외부에 접속하기 위해 보안그룹을 8080 포트로 추가하면 public IPv4 주소:8080 으로 외부에 접속이 가능하다.

  ![AWS Security Group](/post_images/CTFd/CTFd-install/AWS-Security-group.png)

  이제 모든 구성을 마치고 Putty으로 SSH접속하기 위해 키 페어를 만들어준다.

  ![AWS Security key ppk](/post_images/CTFd/CTFd-install/AWS-Security-key-ppk.png)

  이제 인스턴스를 모두 생성하고 Putty에 접속하기 위해 

  [Putty Downloads Link](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

  본인의 운영체제에 맞게 설치하고 PuTTYgen을 실행하고

  ![PuTTY Key Generator](/post_images/CTFd/CTFd-install/PuTTY-Key-Generator.png)

  Load 버튼을 누른 다음 하단의 파일 이름 우측에 PuTTY Private Key Files (*.ppk)를 All Files (*.*) 로 바꾸고 AWS 인스턴스 생성할때 다운로드한 pem 키 페어 파일을 선택하고

  ![Save Private Key](/post_images/CTFd/CTFd-install/Save-Private-Key.png)

  Save private key 버튼을 눌러서 원하는 파일 이름으로 저장하면 ppk 확장자 파일로 만들어집니다.

  이제 SSH연결을 위해 PuTTY실행한 다음 host에 ubuntu@\<AWS instance public IPv4\> 넣고 
  
  PuTTY Category중 Connection -> SSH -> Auth 에 들어가고
  
  Private key file for authentication: 에 있는 Browse... 버튼을 누른 후 아까 만든 ppk파일을 선택한 다음 Open 눌러 연결하면 된다.

  ![PuTTY EC2 instance SSH Connection](/post_images/CTFd/CTFd-install/PuTTY-EC2-instance-SSH-Connection.png)

  이제 모든 구성을 마치고 PuTTY를 이용하여 SSH연결하면 이렇게 접속에 성공한것을 볼 수 있다.

  이제 원하는 명령어를 치면서 CTFd를 구축하면 된다.

  + [Ubuntu에 CTFd 구축](#ubuntu-ctfd-templates-install)
  + [Ubuntu Docker CTFd 구축](#docker-ubuntu-ctfd-templates-install)

<br>

---

<br>

+ ## Ubuntu CTFd Templates Install

  <br>

  1. apt 업데이트 & 업그레이드
  2. CTFd/CTFd git 다운로드
  3. serve.py 구성 편집
  4. python3 설치
  5. serve.py 파일 실행
  6. \<public IPv4\>:8080 CTFd 접속

  <br>

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
  CTFd를 실행할 포트를 변경하기 위해(원하는 포트로 변경)
  
  우측에 있는  ``default=4000`` -> ``default=8080`` 변경하고 

  하단의 ``app.run(debug=True, threaded=True, host="127.0.0.1", port=args.port)`` 를
  
  ``host="127.0.0.1"``  -> ``host="0.0.0.0"`` 으로 바꾼 뒤

  ``ESC -> :wq -> Enter`` 저장한 다음

  만약 python3가 깔려 있지 않은 경우 설치하고 serve.py 파일을 실행하면 된다.

  ```bash
  apt install python3 python3-pip -y
    # python3 python3-pip package install
  python3 serve.py
    # serve.py run
  ```

  ![CTFd-Setup](/post_images/CTFd/CTFd-install/CTFd-Setup.png)

  그러면 이렇게 정상적으로 Ubuntu으로 구축된 CTFd 페이지가 나오게된다.

<br>

---

<br>

+ ## Docker Ubuntu CTFd Templates Install

  <br>

  1. apt 업데이트 & 업그레이드
  2. docker package 설치
  3. docker ctfd/ctfd 이미지 설치
  4. docker 컨테이너 생성 또는 실행
  5. docker CTFd 컨테이너 접속
  6. vim 편집기를 이용하여 host 또는 port 변경
  7. serve.py 실행
  8. \<public IPv4\>:8080 CTFd 접속

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
  ------container------
  root@docker: apt update
    # 사용 가능한 패키지와 버전에 대한 리스트 업데이트
  root@docker: apt upgrade -y
    # 현재 설치되어있는 패키지 최신 버전으로 업그레이드
  root@docker: apt install vim python3 python3-pip -y
    # CTFd 구축을 위한 python3 python3-pip vim 설치
  root@docker: vim serve.py
    # vim 편집기를 이용하여 serve.py 파일 편집
  ```

  docker 컨테이너 안에서 vim 편집기를 이용하여 serve.py 파일을 연 다음 

  ``parser.add_argument("--port", help="Port for debug server to listen on", default=4000)``
  
  4번줄에 위의 코드가 나오는데
  CTFd를 실행할 포트를 변경하기 위해(원하는 포트로 변경)
  
  우측에 있는  ``default=4000`` -> ``default=8080`` 변경하고 

  하단의 ``app.run(debug=True, threaded=True, host="127.0.0.1", port=args.port)`` 를
  
  ``host="127.0.0.1"``  -> ``host="0.0.0.0"`` 으로 바꾼 뒤

  ``ESC -> :wq -> Enter`` 저장한 다음

  ```bash
  python3 serve.py
    # python3 명령어를 이용하여 serve.py 파일 실행
  ```

  serve.py 파일을 실행하고 \<public IPv4\>:8080 으로 접속하면
  
  ![CTFd-Setup](/post_images/CTFd/CTFd-install/CTFd-Setup.png)

  이렇게 정상적으로 CTFd구축에 성공한것을 볼 수 있습니다.
