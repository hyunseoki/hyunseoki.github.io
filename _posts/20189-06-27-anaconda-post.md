---
title:  "Ubuntu18.04 에서 아나콘다 설치부터 실행"
categories:
  - Python
tags:
  - anaconda
---

# Anaconda를 설치한 배경
openslide라는 대용량 이미지 핸들링 라이브러를 깔았다. 2017년 이후 업데이트가 되지 않다 보니, Pillow3.1 이하 버전에서만 동작함. 그래서 기존에 있는 Pillow7 버전을 지우고 다시 깜. 그런데, 이게 왠걸 튜터리얼을 보다보니 온갖 잡다한 라이브러리를 더 깔아야 하고 버전 충돌 문제도 계속 발생함. 이런 문제를 해결하기 위해 평소 호시탐탐 관심을 가졌던 anaconda를 깔기로 함

# Anaconda 소개
하나의 PC에서 여러 개의 가상환경을 제공함. 이 가상환경에 내가 원하는 파이썬 버전, 라이브러리 버전 등을 설치할 수가 있음. 즉, 위와 같이 프로젝트 당 파이썬 버전과 라이브러리 버전들을 바꿔 가면서 작업할 수 있음

# 설치
1. 아나콘다 홈페이지(https://www.anaconda.com/products/individual)에서 sh 파일을 다운 받는다.
2. 설치 디렉터리에서 아래의 명렁어 실행

```
$bash <아나콘다 셸 파일 명>.sh
```

3. 재부팅하고 리눅스 터미널을 키면 conda 동작하여 base가 추작된 것을 확인할 수 있다.
or 터미널 창을 껏다가 킨다. 
or 
```
$cd ~
$~/.bashrc
```


```
(base) user@user:~$
```

# 파이썬 패키지 관리 명령어
- 현재 환경 package 목록 내보내기

```
$pip freeze > requirements.txt
```

- 목록에 있는 패키지 설치하기

```
$pip install -r requirements.txt
```

- 목록에 있는 패키지 삭제

```
$pip uninstall -r requirements.txt
```


# Conda 명령어
- Conda 활성화
: env name을 생략하면 base로 활성화 된다.

```
$conda activate <env name>
```

- Conda 비활성화

```
$conda deactivate
```

- Conda 환경목록 리스트

```
$conda env list
```

- Conda 환경 생성

```
$conda create --name <환경 이름> python=3
```

- Conda 환경 상속하여 생성하기

```
$conda create --name <환경 이름> --clone base
```

- Conda 환경 파일로 저장하기

```
$conda env export -n <환경 이름> --file(-f) <파일이름.yml>
```

- Conda 환경 파일 읽어서 환경 생성하기

```
conda env create -n <환경이름> --file <파일이름.yml>
```

- Conda 환경 삭제

```
$conda remove -name <환경 이름> --all
```