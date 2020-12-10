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

# apt-get -y upgrade
```


다른 언어들을 설치하기 위해 curl이나 wget을 설치하면 좋다. (golang은 wget으로 설치할것임.)
```bash
# apt install curl

# apt install wget
```


wget으로 golang압축파일을 다운로드 받기
(현재 기준으로 go1.15.6버전인데 golang 공식 사이트에 가서 번호만 바꿔서 최신버전으로 받으면 된다.)
```bash
# wget https://dl.google.com/go/go1.15.6.linux-amd64.tar.gz
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

둘중에 뭐가 맞는걸까 뭘까? 일단 해놓긴하겠다.
# export GOPATH=/usr/local/go
# export GOROOT=/usr/local/go
```


설치가 잘 되었는지 확인.
```bash
# go version
go version go1.15.6 linux/amd64
```


go 끗.



다른 터미널로 docker 밖에서 지금까지 설치한 환경들을 image로 중간 저장해주자. (아직 node도 설치할거니까)
```bash
~ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                                      NAMES
194081b67f07        ubuntu:bionic       "bash"                   12 minutes ago      Up 12 minutes                                                                  festive_bohr

~ docker commit -a "leejiwon" -m "ubuntu + curl + wget + golang" 194081b67f07 ubuntu.golang:go

~ docker images
REPOSITORY                                               TAG                 IMAGE ID            CREATED              SIZE
ubuntu.golang                                            go                  f0b3e278932c        13 seconds ago       597MB
```


굳.


다시 docker container에 attach한 터미널로 돌아오자.
맨처음으로 돌아가서 curl로 ubuntu저장소에 새로운 node버전을 땡겨넣어주겠다.
```bash
# cd ~

# curl -sL https://deb.nodesource.com/setup_14.x -o nodesource_setup.sh

# bash nodesource_setup.sh
```

직전에 apt-get update와 upgrade를 해준다.


ubuntu 저장소에 있는 nodejs를 설치해준다
그리고 node 빌드오류를 방지하기위한 build-essential도 설치해준다.
```bash
# apt-get install nodejs

# apt-get install build-essential
```


역시 잘 설치되었는지 확인.
```bash
# node -v
v14.15.1

# npm -v
6.14.8
```



마찬가지로 지금까지의 container 설치된 것을 image로 커밋해주자.
아까 썼던 다른 터미널로 가서,
```bash
~ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                                      NAMES
194081b67f07        ubuntu:bionic       "bash"                   About an hour ago   Up About an hour                                                               festive_bohr

~ docker commit -a 'leejiwon' -m 'ubuntu + go + node' 194081b67f07 go.node:gonode

~ docker images
REPOSITORY                                               TAG                 IMAGE ID            CREATED              SIZE
go.node                                                  gonode              ceeba4e55dc5        About a minute ago   981MB
ubuntu.golang                                            go                  f0b3e278932c        About an hour ago    597MB
```

환경변수는 왜 dockerfile에 잘 안담길까? 다시 찬찬히 살펴봐야겠다.
