# Docker

### **2022 03 06**

## Doker container와 image

Docker 컨테이너를 만들기 위해서는 docker 이미지가 필요하다.

### Docker container

코드와 모든 종속성을 패키지화하여 응용 프로그램이 한 컴퓨팅 환경에서 다른 컴퓨팅 환경으로 빠르고 안정적으로 실행되도록 하는 소프트웨어의 표준 단위이다.

### Docker image

코드, 런타임, 시스템 도구, 시스템 라이브러리 및 설정과 같은 응용 프로그램을 실행하는 데 필요한 모든 것을 포함하는 가볍고 독립적이며 실행 가능한 소프트웨어 패키지다.

<sub>-도커 공식 사이트</sub>

## Dockerfile

`Dockerfile`은 Docker 컨테이너의 환경을 정의해 놓은 파일이다.

```docker
FROM python:3.8-alpine
COPY . /app
WORKDIR /app
RUN pip3 install flask
RUN chmod +x /app/app.py
CND ['python', 'app.py']
```

#### FROM

어떤 리눅스를 사용할 것인지 선택한다.

#### COPY

Docker build를 실행하는 곳의 파일을 /app으로 복사한다. /app은 컨테이너 루트가 아니고 루트에 있는 /app이라는 디렉토리이다.

#### WORKDIR

컨테이너에서 명령어가 실행되는 디렉토리이다. /app에 COPY했기 때문에 /app에서 명령어를 실행한다.

#### RUN

컨테이너를 구성할 파일을 만들 때 사용한다. flask를 설치하고 app.py의 권한을 바꿔주는 명령어를 실행하게 된다.

#### CMD

컨테이너가 실행된 후에 실행할 명령어이다.

## Dockerfile로 build하기

```shell
docker build -t projectName .
```

Dockerfile로 build한다.

Docker image는 아래 명령어로 확인할 수 있다.

```shell
docker images
```

Docker container의 현재 실행되고 있는 프로세스 확인은 아래 명령어로 한다.

```shell
docker ps
```

Docker container를 실행하는 명령어는 아래와 같다.

```shell
docker run -d -p port:port projectName
```

port를 지정해서 컨테이너를 실행한다. 실행하게 되면 `docker ps`로 실행중인 컨테이너 목록을 확인할 수 있다.
