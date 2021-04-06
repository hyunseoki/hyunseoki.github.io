---
title: "리눅스 tar/zip 명령어 정리"
categories:
  - Linux
tags:
  - Linux
  - zip
  - tar
---

## tar/zip 무엇이 다른지, 사용법에 대해 알아보자 

## 1. tar
- tar : 단순히 파일 또는 폴더를 하나의 파일로 묶인 상태  
- tar.gz : 압축이 추가  
- 옵션  

1) -c, --create : tar 파일을 생성  
2) -v, --verbose : 로그 출력  
3) -f, --file [HOSTNAME:]  F : default로 반듯이 있어야 한다. 무슨 의미인지?...
4) -x, --extract : tar 해제
5) -z, --gzip, --ungzip : 압축 옵션  
6) -C, --directory [폴더명] : tar를 해체할 위치 지정

```
$ ## 최소한의 명령어는 다음과 같다. 
$ tar -cf [파일명.tar] [묶일 폴더명]
$ tar -xf [파일명.tar]
$
$ ## 하지만, 실제 사용할 때는 verbose를 같이 넣어주는 편이다. 
$ tar -cvf [파일명.tar] [묶일 폴더명]
$ tar -xvf [파일명.tar] -C [출력 폴더명]
```

## 2. zip 

- 압축하기

```
$ zip [압축파일명.zip] [압축할 파일/폴더명]
```

- 압축풀기
- 옵션

1) -d [압축 푸는 경로] : 특정 경로에 압축 해제

```
$ unzip [압축파일명.zip] -d [폴더명]
```