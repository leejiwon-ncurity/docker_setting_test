# docker_setting_test

docker image에 ubuntu:bionic 이미지 생성해 놓음.
```bash
~ docker pull ubuntu:bionic
```

docker image 확인
```bash
~ docker images
REPOSITORY                                               TAG                 IMAGE ID            CREATED             SIZE
ubuntu                                                   bionic              2c047404e52d        13 days ago         63.3MB
```

docker ubuntu image 실행
```bash
~ docker run -it ubuntu:bionic bash
```

ubuntu 저장소 update와 upgrade (docker내에서는 sudo가 먹히지 않으므로 쓰면 안됨.)
```bash
# apt-get update
Get:1 http://archive.ubuntu.com/ubuntu bionic InRelease [242 kB]
Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Get:3 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [1815 kB]
Get:4 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:5 http://archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Get:6 http://security.ubuntu.com/ubuntu bionic-security/restricted amd64 Packages [236 kB]
Get:7 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 Packages [15.8 kB]
Get:8 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [1370 kB]
Get:9 http://archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages [186 kB]
Get:10 http://archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages [13.5 kB]
Get:11 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages [11.3 MB]
Get:12 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages [1344 kB]
Get:13 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [2243 kB]
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [2134 kB]
Get:15 http://archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages [54.3 kB]
Get:16 http://archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 Packages [265 kB]
Get:17 http://archive.ubuntu.com/ubuntu bionic-backports/main amd64 Packages [11.3 kB]
Get:18 http://archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages [11.4 kB]
Fetched 21.5 MB in 1min 26s (250 kB/s)
Reading package lists... Done

# apt-get -y upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

다른 언어들을 설치하기 위해 curl이나 wget을 설치하면 좋다. (golang은 wget으로 설치할것임.)
```bash
# apt install curl
Reading package lists... Done
Building dependency tree
Setting up publicsuffix (20180223.1310-1) ...
Setting up libssl1.1:amd64 (1.1.1-1ubuntu2.1~18.04.7) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (Can't locate Term/ReadLine.pm in @INC (you may need to install the Term::ReadLine module) (@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.26.1 /usr/local/share/perl/5.26.1 /usr/lib/x86_64-linux-gnu/perl5/5.26 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.26 /usr/share/perl/5.26 /usr/local/lib/site_perl /usr/lib/x86_64-linux-gnu/perl-base) at /usr/share/perl5/Debconf/FrontEnd/Readline.pm line 7.)
debconf: falling back to frontend: Teletype
Setting up libheimbase1-heimdal:amd64 (7.5.0+dfsg-1) ...
Setting up openssl (1.1.1-1ubuntu2.1~18.04.7) ...
Setting up libsqlite3-0:amd64 (3.22.0-1ubuntu0.4) ...
Setting up libkeyutils1:amd64 (1.5.9-9.2ubuntu2) ...
Setting up libsasl2-modules:amd64 (2.1.27~101-g0780600+dfsg-3ubuntu2.1) ...
Setting up ca-certificates (20201027ubuntu0.18.04.1) ...
ib/x86_64-linux-gnu/perl/5.26.1 /usr/local/share/perl/5.26.1 /usr/lib/x86_64-linux-gnu/perl5/5.26 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.26 /usr/share/perl/5.26 /usr/local/lib/site_perl /usr/lib/x86_64-linux-gnu/perl-base) at /usr/share/perl5/Debconf/FrontEnd/Readline.pm line 7.)
debconf: falling back to frontend: Teletype
Updating certificates in /etc/ssl/certs...
138 added, 0 removed; done.
Setting up libk5crypto3:amd64 (1.16-2ubuntu0.2) ...
Setting up libwind0-heimdal:amd64 (7.5.0+dfsg-1) ...
Setting up libasn1-8-heimdal:amd64 (7.5.0+dfsg-1) ...
Setting up libhcrypto4-heimdal:amd64 (7.5.0+dfsg-1) ...
Setting up libhx509-5-heimdal:amd64 (7.5.0+dfsg-1) ...
Setting up libkrb5-3:amd64 (1.16-2ubuntu0.2) ...
Setting up libkrb5-26-heimdal:amd64 (7.5.0+dfsg-1) ...
Setting up libheimntlm0-heimdal:amd64 (7.5.0+dfsg-1) ...
Setting up libgssapi-krb5-2:amd64 (1.16-2ubuntu0.2) ...
Setting up libgssapi3-heimdal:amd64 (7.5.0+dfsg-1) ...
Setting up libldap-2.4-2:amd64 (2.4.45+dfsg-1ubuntu1.8) ...
Setting up libcurl4:amd64 (7.58.0-2ubuntu3.10) ...
Setting up curl (7.58.0-2ubuntu3.10) ...
Processing triggers for libc-bin (2.27-3ubuntu1.3) ...
Processing triggers for ca-certificates (20201027ubuntu0.18.04.1) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.

# apt install wget
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  wget
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 316 kB of archives.
After this operation, 954 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 wget amd64 1.19.4-1ubuntu2.2 [316 kB]
Fetched 316 kB in 3s (115 kB/s)
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously unselected package wget.
(Reading database ... 4574 files and directories currently installed.)
Preparing to unpack .../wget_1.19.4-1ubuntu2.2_amd64.deb ...
Unpacking wget (1.19.4-1ubuntu2.2) ...
Setting up wget (1.19.4-1ubuntu2.2) ...
```

wget으로 golang압축파일을 다운로드 받기
(현재 기준으로 go1.15.6버전인데 golang 공식 사이트에 가서 번호만 바꿔서 최신버전으로 받으면 된다.)
```bash
# wget https://dl.google.com/go/go1.15.6.linux-amd64.tar.gz
--2020-12-09 07:25:19--  https://dl.google.com/go/go1.15.6.linux-amd64.tar.gz
Resolving dl.google.com (dl.google.com)... 172.217.25.78, 2404:6800:4004:818::200e
Connecting to dl.google.com (dl.google.com)|172.217.25.78|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 120951514 (115M) [application/octet-stream]
Saving to: 'go1.15.6.linux-amd64.tar.gz'

go1.15.6.linux-amd64.tar.gz        100%[==============================================================>] 115.35M  19.3MB/s    in 6.2s

2020-12-09 07:25:26 (18.7 MB/s) - 'go1.15.6.linux-amd64.tar.gz' saved [120951514/120951514]
```

Golang은 내가 프로젝트를 만들 폴더를 지정하지 못하고 go자체에서 경로를 정해놨기때문에 해당 경로를 미리 만들어주어야 한다.
/usr/local/경로에 bin, pkg, src 폴더가 필요하다.
```bash
# mkdir -p /usr/local/bin
# mkdir -p /usr/local/pkg
# mkdir -p /usr/local/src
```

그리고 이제 방금전에 받았던 golang압축파일을 /usr/local위치에 풀어준다
```bash
# tar -C /usr/local -xzf go1.15.6.linux-amd64.tar.gz
```

go PATH설정을 해준다
```bash
# export PATH=$PATH:/usr/local/go/bin
```

go 끗.

다른 터미널로 docker 밖에서 지금까지 설치한 환경들을 image로 저장해주자.
```bash
~ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                                      NAMES
194081b67f07        ubuntu:bionic       "bash"                   12 minutes ago      Up 12 minutes                                                                  festive_bohr
```
