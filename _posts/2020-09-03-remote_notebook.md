---
title: "주피터 노트북 원격 서버 열기"
categories:
  - Python
tags:
  - Jupyter
---


# 주피터 노트북 원격으로 접속하기

방화벽 때문인지, 집에서 회사로 ssh 접속이 되지 않아 방법을 찾던 중 주피터 노트북을 이용한 원격 접속 방법을 찾게 되었다. 대부분의 내용은 https://light-tree.tistory.com/111를 참고 하였다. 

## 0. 방화벽 해제하기

- 참고 22번은 이미 ssh에서 사용 중

```
$ sudo ufw allow 8888
```

## 1. 서버 셋팅 설정

- config 생성 : 다음 명령을 실행하면 /home/hyunseoki/.jupyter 디렉토리에 jupyter_notebook_config.py 파일이 생성된다.

```
$ jupyter notebook --generate-config
```

- 비밀번호 및 해시 생성 :

```
$ Ipython

In [1]: from notebook.auth import passwd                                        

In [2]: passwd()                                                                
Enter password: 
Verify password: 

Out[2]: 'sha1:fe2fa66e1679:cb12b720b5e6fc5310714dadb7c048b2426efd82'

```

- config 파일 수정 : /home/username/.jupyter/jupyter_notebook_config.py 파일 맨 위에 다음 내용을 추가한다.

```
c = get_config()
c.NotebookApp.allow_origin = '*' // 외부 접속 허용
c.NotebookApp.notebook_dir = u'/home' 
c.NotebookApp.ip = 'IP주소'
c.NotebookApp.port = 8888
c.NotebookApp.password = u'sha1:fe2fa66e1679:cb12b720b5e6fc5310714dadb7c048b2426efd82'
c.NotebookApp.open_browser = False
```

## 2. 서버 시작하기

- 서버 시작

```
$ cd /home/hyunseoki/.jupyter
$ jupyter notebook --config jupyter_notebook_config.py
```

## 3. 서버 접속하기

- 브라우저에 IP주소:포트 입력하면 접속됨