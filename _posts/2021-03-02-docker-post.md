---
title: "Docker 명령어"
categories:
  - Setting
tags:
  - Docker
---

# Docker

자주 사용하는 Docker 명령어

## 1. Container

### 1-1. 생성

```
$ docker run <옵선><이미지 이름><컨테이너 실행 시, 기본 실행 명령어>
$ docker run -it --gpus all -p 8888:8888 -v my_project:my_project --name ubuntu /bin/bash
```

- 옵션 
1) -i interactive
2) -t Pseudo-tty
3) -p [도커 포트:컨에이너 포트]
4) --name [생성할 컨테이너 이름]
5) --gpus [사용할 gpu]
6) -v [host 폴더][컨테이너 폴더]

### 1-2. 접속
```
$ docker attach <container_id>
```
- 종료 : exit 또는 ctrl+D
- 컨테이너는 그대로 두고, 터미널만 빠져나오기 : ctrl+P, ctrl+q

### 1-3. 삭제

```
$ docker rm <container_id>
```

### 1-4. 목록 출력

```
$ docker ps -a
```

### 1-5. 시작

```
$ docker start <container_id>
```

### 1-6. 정지

```
$ docker stop <container_id>
```

### 1-7. 재시작

```
$ docker restart <container_id>
```

## 2. Image

### 2-1. 빌드

```
$ docker build <옵션><Dockerfile 경로>
```

- 옵션 
1) --tag [hello:0.1]


### 2-1. Image Hub에서 이미지 받기

```
$ docker pull <이미지 이름>:<태그>
```

### 2-2. Image 목록 출력

```
$ docker images
```

### 2-3. Image 삭제

```
$ docker rmi <이미지 id>:<태그>
```


