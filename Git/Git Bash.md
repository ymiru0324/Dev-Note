# Git Bash

Git의 기능을 풍부하게 사용하고 싶으면 Git CLI를 사용하는것이 좋다.

### 간단한 Git Bash 사용법

- Branches 제외

---

## repo 생성 후 push

> 현재 디렉토리 확인
> 

```bash
pwd
```

> 현재 디렉토리의 파일 디렉토리 확인
> 

```bash
ls
```

> 해당 경로에서 파일 목록 확인
> 

```bash
ls -al
```

> 경로이동
> 

```bash
cd [경로명]
```

![1.PNG](Git%20Bash%20ecf029893b6d4ac3a44f4729c761303c/1.png)

- 본인이 원하는 경로 들어가서 파일 주소 복사하시고 드라이브 이름 앞에 : 지우고 \만 /로 고치시면 됩니다 / Ex) D:\workspace\git-test → cd D/workspace/git-test

```bash
cd D/workspace/git-test
```

---

> 해당 경로에서 git을 시작 git init시 파일 목록에서 .git 생성
> 

```bash
git init
```

> ID와 E-Mail 설정하기
> 

```bash
git config --list
```

```bash
git config --global user.name "Github ID"
git config --global user.email "Github E-Mail"
```

> git의 현재 상태
> 

```bash
git status
```

![2.PNG](Git%20Bash%20ecf029893b6d4ac3a44f4729c761303c/2.png)

빨간색 부분은 버전 관리가 되고 있지 않음

> version을 만들기 위한 준비
> 

```bash
git add .
```

> git의 현재 상태
> 

```bash
git status
```

![3.PNG](Git%20Bash%20ecf029893b6d4ac3a44f4729c761303c/3.png)

git add . 이후로 달라진 모습

> version 생성
> 

```bash
git commit -m “msg”
```

![4.PNG](Git%20Bash%20ecf029893b6d4ac3a44f4729c761303c/4.png)

version 생성

> version 생성 확인 (commit 내역 확인)
> 

```bash
git log
```

![5.PNG](Git%20Bash%20ecf029893b6d4ac3a44f4729c761303c/5.png)

---

## 변경사항 발생시 version 생성

```bash
git status
git add.
git commit -m "msg"
git log
```

![6.png](Git%20Bash%20ecf029893b6d4ac3a44f4729c761303c/6.png)

---

## 원격 저장소 등록

(깃허브에 repo 생성 후 진행할 것)

```bash
git remote add origin [repo 주소]
```

> 위의 원격 저장소의 경로로 push
> 

```bash
git push origin master
```