# 1. 소스코드 변경사항 관리방법
### 1-1. 커밋 하나에 반영되는 내용
- 커밋하려는 대상을 Changeset이라고 부름
- Workspace의 변경사항을 Stage 영역에 add하지 않으면 Changeset에 포함되지 않음
![image](https://user-images.githubusercontent.com/99636945/204939646-241481ad-3a84-47fb-84ad-0dbf7e611701.png)

### 1-2. 특정 소스코드의 위치에서의 상태가 다른 경우
- 아래와 같은 과정으로 진행된다.  
![image](https://user-images.githubusercontent.com/99636945/204940757-eb77f291-2b08-4b72-bc5d-8eb1972cb669.png)
![image](https://user-images.githubusercontent.com/99636945/204940826-6f313a92-08ae-410b-842e-fa9c492ebea6.png)
![image](https://user-images.githubusercontent.com/99636945/204940884-2b9c076a-a251-4530-bfc7-d781dc31f3d0.png)

# 2. Push 명령어
- Local Repository에 있는 내용을 Remote Repository로 반영해야할 경우가 있다.
- git push 명려어를 사용한다.
- 아래와 같이 동작한다.  
![image](https://user-images.githubusercontent.com/99636945/204941153-79e97fbd-2aac-4533-8c9b-5fc025fdf57f.png)

# 3. Branch
- Local Repository에서 개발하던 중 Remote Repository에 부분적으로 반영해야 하는 경우
- 아래와 같은 두 가지 문제점이 존재한다.
- 1. 미완성된 코드가 원격 저장소로 올라가는 상황 발생-> 다른 개발자가 pull 받아 실행 시 문제 발생 가능성
- 2. git commit을 의미 단위로 저장해야 하는 원칙에 위배됨  
![image](https://user-images.githubusercontent.com/99636945/204941603-6a94648b-71c6-4f2c-9707-1242bab59774.png)
- 이를 해결하기 위해서 branch를 사용한다.
- 내 수정사항을 특정 공간에 고립시켜 다른 사용자의 변경사항과 섞이지 않게 하고 서로 영향을 받지 않도록 만듬  
![image](https://user-images.githubusercontent.com/99636945/204941714-3cd16fa7-0344-45e0-8db2-93786c5e9863.png)
- 서로 다른 개발자가 서로 다른 기능을 동시에 개발하는 상황에서 유용하게 활용
- 기본으로 주어지는 main 브랜치가 있고, 그 외에는 생성에서 사용해야 함  
![image](https://user-images.githubusercontent.com/99636945/204941856-eb20b11a-f3f9-4648-ba61-e1af1bd6334e.png)

### 3-1. branch 실체
- 특정 Commit을 가리키는 단순한 pointer 역할을 함  
![image](https://user-images.githubusercontent.com/99636945/204942057-f1be5e68-5b99-4bed-a7af-0cb726c7ab9a.png)
- 하나의 Repository에 여러 branch가 있기 때문에, 내가 어떤 branch에서 작업 중인지 알기 위한 방법이 필요
- 내가 현재 어떤 branch를 사용하는지 알기 위해서 Head라는 개념을 사용
- Head는 브랜치에 대한 포인터이며, checkout명령어 사용시 포인터가 가리키는 Branch가 변경됨
- 예를 들어 main branch에서 작업을 한다고 가정하자.  
![image](https://user-images.githubusercontent.com/99636945/204942200-0e2b2e14-d7ce-4776-8207-697b0df87236.png)
- 여기서 Commit을 하나 더 생성하면, HEAD 포인터가 가장 마지막 커밋으로 이동하게 되며, 커밋을 수행할 때 마다 반복된다.  
![image](https://user-images.githubusercontent.com/99636945/204942266-63a704ba-3022-4f7c-8478-c7893853010f.png)

### 3-2. 브랜치 응용
- 하나의 git repository는 여러 개의 branch를 가질 수 있음
- 각 branch는 특정 commit에 대한 포인터 그 이상 그 이하도 아님
- 생성은 git branch -c 또는 git checkout -b로 진행하고 이동은 git branch 또는 git checkout으로 진행한다.
![image](https://user-images.githubusercontent.com/99636945/204942604-ceb51848-69a5-4ed0-afd9-799865eeb289.png)
- 브랜치 생성 시, 위에 언급한 것 뿐만이 아닌 다른 방법도 존재한다.
- git branch [브랜치 이름] [가리킬 commit ID]로 최신 커밋이 아닌, 다른 커밋을 가리키게 할 수도 있다.
- 브랜치 이동 시 주의해야 할 점은 workspace가 clean상태여야 한다는 것이다.
- checkout -b 옵션을 사용하면 브랜치를 생성함과 동시에 해당 브랜치로 이동한다.

### 3-3. 브랜치의 동작 방식
- 두 브랜치가 있다고 가정했을 때, 한 브랜치에서 Commit을 진행하면 해당 브랜치의 HEAD 포인터가 이동한다.
![image](https://user-images.githubusercontent.com/99636945/204942958-f76c98af-4c83-4362-87a0-3398cbed8e7b.png)
- 이후 다른 브랜치에서 Commit을 진행하면, 가장 최신 커밋을 기준으로 커밋에 분기가 생성된다.
![image](https://user-images.githubusercontent.com/99636945/204943249-35478651-74b1-4025-9dc0-62f26e623109.png)

### 3-4. 브랜치 삭제
- git branch -d [브랜치 이름] 으로 삭제한다.
- 강제 삭제는 git branch -D [브랜치 이름] 으로 실행한다.
- 기본적으로 변경 사항이 존재하면 브랜치를 삭제할 수 없기 때문이다.

# 4. Merge
- 3-3. 에서 언급된 분기와 관련된 내용이고, 분기하여 작업했던 내용을 합치는 과정이다.
- 독립된 branch에서 작업을 수행하고 각 branch에서 작업한 내용을 다른 branch에 통합 및 병합하면 된다.
- 분기 후 병합의 최종 결과물은 다음과 같이 나온다.  
![image](https://user-images.githubusercontent.com/99636945/204943523-80f1979a-2042-4c13-b4f7-a0cf15abd728.png)
- 병합의 방법은 기본적으로는 두 가지가 있다. 그 외에는 rebase, squash 등이 있다.

### 4-1. Fast-forward merge
- 기본적인 병합 방법의 일종이다.
- 병합하려는 branch들 사이에 분기가 존재하지 않을 경우 사용된다.  
![image](https://user-images.githubusercontent.com/99636945/204943771-5a893fe6-7fa6-4b8a-b9c6-a9c01f9686a8.png)
- featureA의 내용을 main으로 반영하기 위해선 main branch에서 merge 작업을 한다.
- git merge [브랜치 이름]을 실행하면 기본 옵션으로 fast-forward 병합을 진행한다.  
![image](https://user-images.githubusercontent.com/99636945/204943929-56001b68-c68b-493b-a236-84be474301b2.png)

### 4-2. 3-way merge
- 병합하려는 branch에 존재하는 changeset들이 특정 branch에만 존재하는 경우
- 가장 많이 발생하는 상황이다. 여러명의 개발자들이 하나의 소스토드 베이스에서 여러 브랜치로 작업하기 때문이다.
- 아래 상황을 가정하자.  
![image](https://user-images.githubusercontent.com/99636945/204944241-2d4d36d6-cf06-4ff1-9958-854bfafe4c7d.png)
- 아래와 같은 방법으로 병합을 진행한다.  
![image](https://user-images.githubusercontent.com/99636945/204944319-0f1a1e36-a861-43ef-a2b0-121edbabb907.png)
![image](https://user-images.githubusercontent.com/99636945/204944465-317287fd-0c1c-490e-a6c8-71dbf2cd7c25.png)
![image](https://user-images.githubusercontent.com/99636945/204944487-c6cc9ec9-db2d-46cb-85f6-73855cc644f8.png)
- 로그 출력 방법의 부가 사항은 아래를 참조하도록 하자.  
![image](https://user-images.githubusercontent.com/99636945/204944650-0dc0488d-e88e-4068-96d3-eba64164a44a.png)

### 4-3. Merge Conflict
- 병합 수행 과정에서 분기가 발생한 base를 기준으로 병합하려는 두 branch에 동시에 존재하는 file의 특정 내용을
서로 다른 내용으로 수정한 경우 git에 의해 자동 merge가 되지 않음
- 소스코드의 의미를 알지 못하기 때문에 판단할 수 없음  
![image](https://user-images.githubusercontent.com/99636945/204945235-f9cacea0-4afb-438e-929f-d2360e23fbb3.png)
- 변경사항 확인 시 소스코드의 Line 단위로 파일 비교가 되므로 서로 다른 Line의 변경사항에 대해선 Conflict가 발생하지 않음
- 변경이 발생한 부분과 최소 한 줄 이상은 떨어져야 충돌이 발생하지 않음

### 4-4. Fast-foward merge conflict
- 병합하려는 branch들 사이에 분기가 없을 때 사용되므로, conflict가 발생할 수가 없음
- 새로 생성한 브랜치에는 기존 브랜치의 변경 사항이 이미 포함되어 있기 때문이다.

### 4-5. 3-way merge conflict
- 병합하려는 branch에 존재하는 Changeset들이 특정 branch에만 존재하는 경우 충돌 발생 가능성이 존재
- branch들 간의 분기가 발생할 수 있는 구조이기 때문이다.

### 4-6. Merge Conflict 해결
- 가장 간단한 방법은 merge 수행자가 직접 변경사항을 대조하여 적절한 것을 선택하고 필요 시 추가 수정 작업하여 반영하는 것
- merge conflict가 발생하면 git에서 marker를 해당 파일에 추가하여 서로 다른 변경사항을 표시함
- 이를 바탕으로 서로 다른 변경사항을 적절히 합쳐서 conflict를 해결해야 함

# 5. Rebase
- Branch에서 작업을 진행하는 동안 해당 branch 생성 시점 이후로 main branch의 변경사항이 많이 발생하거나 버그 수정 등
중요한 내용이 main branch에 반영되었을 때 사용하는 merge 방식
- Main Branch에 새롭게 변경된 내용을 먼저 해당 branch로 반영 후 해당 branch의 작업이 완료되었을 때 다시 main branch로 병합 가능  
![image](https://user-images.githubusercontent.com/99636945/204948902-2f3dc154-3675-45c5-9137-fa6513ca1a42.png)

### 5-1. 동작 방식
- 다른 브랜치에서 기능 개발 중 기존 소스코드 버그로, 중단된 상황을 가정  
![image](https://user-images.githubusercontent.com/99636945/204948972-0c370946-8513-42c6-a728-0bfd64ccc2a4.png)
![image](https://user-images.githubusercontent.com/99636945/204948992-664646ea-a0c6-47aa-98ca-5ebf2445d009.png)
![image](https://user-images.githubusercontent.com/99636945/204949232-028c127f-39b0-4cbf-95ea-444d1202add9.png)
- rebase 시 featureA 브랜치에서 진행

# 6. Squash
- 기능 개발을 위해 생성한 branch에서 작업하던 중 중간중간 진행사항을 임시 저장하는 경우가 있으며, 커밋 메시지를 크게 신경쓰지 않고 입력하게 됨
- 이러한 commit은 의미가 없으며, 개별 commit으로 반영되어선 안됨
- merge 수행 시 임시 commit을 제거하고 의미 단위인 Commit message 구성을 위해 모든 commit을 하나의 commit으로 변환하여 반영
![image](https://user-images.githubusercontent.com/99636945/204950459-aa464bb4-dd8b-4f60-b68a-944ef254850b.png)

### 6-1. 동작 방식
- 별도 생성한 branch에서 발생한 commit들을 모두 하나로 묶어서 별도의 commit 생성하며 합쳐지기 이전 commit들은 log에서 확인되지 않음  
![image](https://user-images.githubusercontent.com/99636945/204950617-d91eadc0-632a-4c5b-b67e-cd9d049b0beb.png)
- 명령어는 main branch로 이동 후 git merge --squash 옵션을 덧붙인다.  
![image](https://user-images.githubusercontent.com/99636945/204950698-47aab1f6-16b0-46b0-aeff-81897732a9d6.png)

### 6-2. 3-way merge와의 차이점
- squash는 joint commit이 아닌 완전히 별도의 commit을 생성하게 됨
- git log를 통해 차이점 확인 가능  
![image](https://user-images.githubusercontent.com/99636945/204951266-86f72120-32f8-4586-be72-2019c50f868f.png)

# 7. Git을 이용한 협업
- Git Repository를 local PC에 clone하면 원격 저장소를 그대로 복사해서 download 하는 것
- clone을 수행한 remote repository를 origin 이라는 이름으로 참조하게 됨
![image](https://user-images.githubusercontent.com/99636945/204954874-1a46585d-6299-4fee-b8f4-3d84e6e53004.png)
- clone 직후에는 workspace 가 clean 상태고, main branch는 remote와 동일한 상태를 가짐
- git log를 통해 clone 시점의 origin의 main branch의 commit을 확인할 수 있음
![image](https://user-images.githubusercontent.com/99636945/204955779-3ab0b113-299a-4534-bef7-9b88d3f16c2e.png)
- origin/HEAD는 origin에서 설정된 default branch를 가리키고 Local의 HEAD 포인터와는 다른 역할임

### 7-1. Local Repository 에서 생성한 Branch 업로드
- 명령어로는 git push [remote repository] [branch name]를 통해 원격 저장소에 브랜치를 업로드한다.  
![image](https://user-images.githubusercontent.com/99636945/204956055-cf3cf308-77d4-463a-8902-ed8353f67330.png)
- 로컬 저장소의 origin/main과 origin/HEAD는 clone할 당시 시점의 값을 저장하고 있음  
![image](https://user-images.githubusercontent.com/99636945/204956186-74d4bd74-8ff1-4236-b2ee-9541be81302f.png)
- 원격 저장소에 변경된 내용을 다시 로컬 저장소로 동기화해야 origin/main이 현재 원격 저장소의 상태와 동일해짐  
![image](https://user-images.githubusercontent.com/99636945/204956515-91e46057-3250-4b83-97b5-18f03f90421a.png)
  
### 7-2. 지역/원격 저장소 동기화 흐름
- 1. Clone 직후  
![image](https://user-images.githubusercontent.com/99636945/204956714-8f38031a-09bf-4ffc-998e-d0d5b00b9100.png)
- 2. Remote에 다른 개발자로부터 변경사항 반영된 후
![image](https://user-images.githubusercontent.com/99636945/204956802-d7c14ff0-501a-404a-a0a7-a1637cc12943.png)
- 3. Git fetch 명령어로 remote에 변경된 내용을 local repository로 동기화 한 후
![image](https://user-images.githubusercontent.com/99636945/204956881-eeca7ec4-0085-4187-ace3-15c38ee52e33.png)
- 4. Git merge 명령어로 origin/main의 내용을 main에 반영한 후
![image](https://user-images.githubusercontent.com/99636945/204956958-980e4a11-f0f9-4d8b-9fd7-22662e53d924.png)
- 3, 4는 fetch, merge와 관련된 것인데, 이를 한꺼번에 자동으로 수행하는 명령어는 git pull origin main이다.
- fetch 및 merge는 pull로 변경사항을 자동으로 내려받을 수 없는 환경일 경우 유용하게 사용할 수 있다.

### 7-3. Push/Fetch
- git push 명령어의 경우 branch 단위로 동기화 진행
- git fetch 명령어의 경우 모든 branch에 대해서 새로운 내용으로 update한다.  
![image](https://user-images.githubusercontent.com/99636945/205201164-f67833a3-df18-48c4-9a98-4340e8eb2f30.png)
- 이 때 기본적으로 Fast-forward 방식으로 merge를 시도함
- 되지 않으면 push는 실패, 사용자가 로컬 저장소를 remote의 최신 상태로 업데이트 후 직접 merge하고 다시 push로 동기화해서 Fast-forward merge가 되도록 해야함
- Push 명령어는 Fast-forward merge가 가능할 때에만 동작한다는 의미임

### 7-4. 성공적인 Push
- 성공적으로 Push되는 상황은 다음과 같다.  
![image](https://user-images.githubusercontent.com/99636945/205203822-0f483f58-c91d-4c42-9581-c07bd170a09a.png)
![image](https://user-images.githubusercontent.com/99636945/205203863-c034c544-88df-44c3-9a91-7b365177ae26.png)
![image](https://user-images.githubusercontent.com/99636945/205203887-e681bc13-50de-4efb-85d8-f309f23529ec.png)
![image](https://user-images.githubusercontent.com/99636945/205203910-2ad49aa0-200a-4fac-801c-de406d3276f0.png)

### 7-5. 실패한 Push 및 해결
![image](https://user-images.githubusercontent.com/99636945/205204239-fb625b2d-412d-475d-b661-9b532eeed410.png)
![image](https://user-images.githubusercontent.com/99636945/205204285-3dff232b-8665-46c2-90af-f6f82feb6a74.png)
![image](https://user-images.githubusercontent.com/99636945/205204315-94902795-6766-412a-a543-2ce837a873e1.png)
![image](https://user-images.githubusercontent.com/99636945/205204335-dff6aaa0-9573-4a72-a913-8865d1150f23.png)
![image](https://user-images.githubusercontent.com/99636945/205204556-2f5ecb7e-8210-46bb-8d6a-def807c07a4e.png)
- 실패하는 이유는 개발자 A가 생성한 C3, 개발자 B가 로컬에 생성한 C4는 3-way merge 방식으로 병합해야 하기 때문임
- 개발자 B 입장에서는 push에 실패해도 영향이 없고 다음 작업을 진행하면 됨
![image](https://user-images.githubusercontent.com/99636945/205204824-4070006f-1496-4701-8773-812a39300935.png)
![image](https://user-images.githubusercontent.com/99636945/205205331-d1216096-9107-4701-999d-0a0fbf8ce615.png)
![image](https://user-images.githubusercontent.com/99636945/205205402-9ad355db-4e4a-4f51-b8ad-36e0b7bea6d1.png)
![image](https://user-images.githubusercontent.com/99636945/205205455-132bc1d1-3e7e-48af-ae0e-ec5179325b03.png)

### 7-6. 실패한 Push 및 해결(2)
![image](https://user-images.githubusercontent.com/99636945/205205716-63f36c5a-04c2-454e-9fae-c2fd646cfd34.png)
![image](https://user-images.githubusercontent.com/99636945/205206142-853a3bed-dcb8-408b-b52e-424b7d60a05f.png)
![image](https://user-images.githubusercontent.com/99636945/205206158-667f4198-0124-411d-b1af-f41204eab4fb.png)




