# EGit

Eclipse에서 Git을 사용하는 것

Window - Show View - Other - Git Repositories

Window - Show View - Other - Git Staging

Window - Show View - Other - History

```
SCM Software Configuration Management
- 코드추적(버전관리) 외에 build, packaging, deploy등 프로젝트 관련 프로세스를 관리

VCS Version Control System
- 프로젝트 작성 / 수정 / 보완에 따른 변경내역을 버전으로 관리

버전관리 프로그램
- server-client : 중앙저장소를 공유한 각각의 클라이언트(개발자)에서 저장소의 일부만 가져와서 작업 후, 중앙 저장소에 반영
		- subversion
- 분산형 : 참여하는 각각의 클라이언트에서 전체저장소에 대한 복제본을 가지고 작업
 		- git
```

![1](https://user-images.githubusercontent.com/81818730/167451247-0ce8cd9f-5018-4a1e-81cd-28c40f8814a1.PNG)


## Git 시작

Project 우클릭 - Team - Share Project

→ Use or create repository in parent folder of project 체크 해제

→ Create 후 적당한 곳에 폴더 생성 후 지정

→ Project 체크 후 Finsh

→ Project 선택 후 Alt + Enter - Location 으로 위치 확인 가능

## .gitignore

.gitignore에 작성된 파일은 버전관리 하지 않겠다.

※ 컴퓨터마자 설정 파일이 다르기 때문에 협업시 필수 사항

gitignore를 대신 생성해주는 사이트

[gitignore.io](https://www.toptal.com/developers/gitignore)

## Git Commit
![2](https://user-images.githubusercontent.com/81818730/167638483-660b4757-b207-4395-9cce-489fece3a059.png)
![3](https://user-images.githubusercontent.com/81818730/167638490-5227d6ae-5429-49bd-b575-1e91537e588d.png)



변경 사항 저장후 Commit시 History에 출력됨

## Branch

> 프로젝트명 옆에 Branch 이름이 뜨니 잘 살펴보도록 하자 !
> 

![4](https://user-images.githubusercontent.com/81818730/167451336-a4ffcc38-9fc4-4f42-b6e3-23a010b7a7bd.PNG)


> 프로젝트 우클릭 - Team - Switch To - New Branch - Check out new branch (브렌치 변경)
> 

animal Branch 생성 후 변경 사항 저장 후 Commit

![5](https://user-images.githubusercontent.com/81818730/167638513-253bd56c-1e10-474d-9e25-f45b66b7d9df.png)



변경 사항이 적용 됨 !

![6](https://user-images.githubusercontent.com/81818730/167638532-38d20eec-f0b9-4b28-8bfa-2531da7f3216.png)


> master Branch로 변경시 변경 사항 적용 안되어 있다. (별개로 나누어서 작업 가능)
> 

## Merge

Merge의 주체인 Branch로 Check Out 후 Merge할 Branch를 Merge한다

Ex) Animal Branch의 변경 사항을 Master에 적용하고 싶다면 Master로 Switch 한 후 Animal Branch를 클릭 후 Merge 함

> 프로젝트 우클릭 - Team - Merge
> 
- fast-forward-merge : Merge하고자 할 Branch가 현재 Branch를 온전히 포함한다. / Merge할 Branch가 기존 Branch(master)의 주체에서 그대로 따라나온 것 / 새로운 버전이 만들어지지 않음
- non-fast-forward-merge : 기존 Branch의 주체(master)도 변경사항이 있는데 다른 변경 사항이 있는 Branch를 Merge할 때 / 새로운 버전이 만들어지면서 병합이 된다.
- fast-forward-merge 방식이 안전하며 non-fast-forward-merge도 영역이 다르다면 충돌은 일어나지 않지만 영역이 같을때, 충돌이 일어날 수 있다

### fast-forward-merge

새로운 버전이 만들어지지 않았다. 

Merge하고자 할 Branch가 현재 Branch를 온전히 포함하였기 때문

![7](https://user-images.githubusercontent.com/81818730/167638545-0a1df605-fec1-4288-b39c-d56a2c1c6d35.png)


### non-fast-forward-merge

새로운 버전이 만들어졌다.

기존 Branch의 주체(master)도 변경사항이 있는데 다른 변경 사항이 있는 Branch를 Merge하였기 때문

> animal Branch에 변경사항 적용 후 커밋한 다음, master Branch로 Check Out 하여 mater Branch에서 bugfix Branch 생성 후 bugfix Branch의 변경 사항을 저장 하여 fast-forward 방식으로 master Branch에 merge한 후 다시 master Branch로 Check Out하여 animal Branch의 변경 사항을 master Branch에 Merge한 상황.
> 

한마디로 변경사항이 일어난 Branch에 변경 사항이 일어난 Branch를 merge 하였을때 !

![8](https://user-images.githubusercontent.com/81818730/167638557-ed0f5c7e-d9ba-4a35-924a-882a73a687cb.png)
![9](https://user-images.githubusercontent.com/81818730/167638574-ffa49432-5416-454a-94b5-a53df383e5b8.png)
![10](https://user-images.githubusercontent.com/81818730/167638580-46c1b446-4a65-4402-aae5-17252cc347ab.png)



복잡하지만 하다보면 이해 되고, 자주 일어나는 상황이다 !

### 같은 위치에 다른 코드를 작성 한 서로 다른 Branch를 Merge하였을 때

보통 Line은 중요하지 않고, 내용에 따른 충돌 사항이 일어난다

![11](https://user-images.githubusercontent.com/81818730/167451419-5713f17b-bc72-4a53-ba4f-100fa2d99277.PNG)


버전이 합쳐지지 않고, 전부 채결한 뒤 Merge 하면 해결된다 

![12](https://user-images.githubusercontent.com/81818730/167638613-aa04a009-807f-4a94-ba60-662acca37898.png)



채결하고 나면 이러한 Commit 메세지가 작성된다

![13](https://user-images.githubusercontent.com/81818730/167638630-810a8983-542e-4fb1-96a6-4b45a278c137.png)



<aside>
⚙ Master는 완성된 코드만을 모으는 곳이라고 생각하면 편하고, 새로운 작업이 있을때 마다 Branch를 따서 작업이 완성되면 Master에 Merge 해주는게 이상적인 방법이다.

</aside>

## Github 최초 등록

한마디로 local_repo 에서 remote_repo로 Push 해준다.

Github에 repo 생성 → 원격 저장소 주소 복사 → Eclipse → Git Repositories → Remotes - Configure push → Change → URL 등록 → Authentication에 User와 Password에 [Token](https://github.com/ymiru0324/Dev-Note/blob/main/Git/Token.md) 값을 입력해준다 ! → Advanced (Push 설정에 대한 설정 / Branch별로 연결을 도와주는 설정) → All Branches → Finish ! → push → Github repo 이동하여 잘 들어갔는지 확인

![16](https://user-images.githubusercontent.com/81818730/167638924-4778ca86-ed22-4ff8-92f4-63a533f6ae22.png)



Remotes에 연결이 되었다

상단의 내려 받는 주소는 fetch(download), 상단의 올려 주는 주소는 push(upload)

## push/fetch

### push

변경사항 저장후 commit → 프로젝트 우클릭 → Team → Push to origin

![17](https://user-images.githubusercontent.com/81818730/167638661-228cc8aa-0201-4cc4-9fc8-79154945c0ee.png)



이런 메세지가 뜬다면 성공

### fetch

Branch들을 지역 Branch로 바로 가져오지 않고 remotes/branch이름 으로 가져온다. 한마디로 3개의 브렌치가 있는 repo를 fetch할 시 3개의 Bracnh가 복사되어 총 6개의 Branch를 fetch한다.

<aside>
⚙ 왜? 
remotes/branch는 원격저장소에 대한 읽기 전용 Branch이다.

</aside>

저장된 변경사항을 Configure Fetch → Advanced (Fetch설정에 대한 설정 / Branch별로 연결을 도와주는 설정) → All Branches → Finish ! → fetch

![18](https://user-images.githubusercontent.com/81818730/167451539-a9681465-e017-4f7f-bdfc-f07d94814ce7.PNG)


→ Remote Tracking에 Branch가 뜨는것을 확인하고 적용할 Branch에 Remote Tracking Branch를 Merge 하고나면 성공

## pull

fetch와 Merge를 한방에 해결

![19](https://user-images.githubusercontent.com/81818730/167451550-28eec1f1-1924-4d85-b980-54bf6698596c.PNG)


프로젝트 우클릭 - Team - Pull (Pull...은 설정 변경해서 할때 사용)

![20](https://user-images.githubusercontent.com/81818730/167638782-10671885-dbdc-458f-83b2-bae56f4b3ff9.png)



## reset/revert

```
reset : 지정 버전으로 돌아감
- hard : 이후 변경사항 모두 제거
- mixed : 이후 변경사항을 unstaged changes에서 관리
- soft : 이후 변경 사항을 staging area에 추가

revert : 지정한 버전의 취소 버전을 새로 추가
- history를 변경할 수 없는 경우 유용하다.
- conflict 발생 가능성 있음
```

### reset

History → 돌아가고 싶은 버전 우클릭 → Reset → hard/mixed/soft 중 선택 (보통 hard)

※혼자 작업할 때는 괜찮지만 협업시에는 상당히 위험하다

### revert

History → 취소하고 싶은 버전 우클릭 → Revert

![21](https://user-images.githubusercontent.com/81818730/167451567-a27fc0b0-bd1b-4371-88e3-8f92f72363b3.PNG)


현재 버전과 없는 버전이 충돌 !

→ Revert된 버전과 없는 버전을 합쳐서 Commit 해주면 됨
