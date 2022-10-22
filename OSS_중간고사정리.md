# 1. 버전관리, 깃 개요
### 1-1. 버전 관리의 필요성
- 이전에는 파일의 이름을 수정해가면서 관리해왔다.
- 여러 이름의 새 폴더에 여러 파일을 복사해 관리했다.
- 즉 관리할 파일이 많다면 디스크의 용량을 매우 많이 잡아먹는 단점이 존재
- 버전 관리는, 한 파일에 대한 버전을 관리하기 때문에 디스크를 많이 먹지 않는다.

### 1-2. 버전관리 시 필요한 정보
- 누가
- 저장소가 여러 개인 경우 어느 저장소에서 했는지
- 어느 파일을
- 언제
- 어디를
- 어떻게
- 시간의 흐름에 따라 파일 집합에 대한 변경 사항을 추적 관리한다.

### 1-3. 버전 관리의 Commit
- 적어두다 라는 의미를 가진다.
- 저장소의 현 상태를 저장하는 행위이다.
- 파일 집합의 변경 내용을 깃 저장소에 기록하는 작업이 Commit이다.
- 수정된 점이 없다면, 파일을 새로 저장하지 않는다.

### 1-4. 저장소
- 파일이나 폴더를 저장하는 곳으로 원격과 지역 저장소로 나뉜다.
- 원격 저장소 : 원격 저장소 전용 서버에서 파일을 관리하며, 여러 사람이 함께 공유 가능
- 지역 저장소 : 내 PC에 파일이 저장되는 개인 전용 저장소
- 원격 -> 지역으로 변경내역 가져오기 : git pull
- 지역 -> 원격으로 변경내역 올리기 : git push
![image](https://user-images.githubusercontent.com/99636945/197132491-69bb7162-aadf-4b11-8a58-d3f687b9401d.png)

### 1-5. 깃 개요
- 리누스 토발즈가 2005년에 개발함.
- 장점으론 모든 개발자는 지역 시스템에 코드의 전체 사본을 소유할 수 있다.
- 컴퓨터 파일의 변경을 추적하는데 사용된다.
- 여러 개발자가 함께 협업하고, 변경 사항을 추적하고, 분산 버전 제어 도구, 평행 분기 등 비선형 개발을 지원한다.
- 기록 추적, 백업 생성, 협업 지원, 분산 개발, 비선형 개발을 지원하고, 자유 및 오픈소스 관리에 적합하다.

### 1-6. 깃의 구조
- Git에는 GUI, CUI 인터페이스가 있다.
- Git CUI는 Git Bash가 있다.
- Git Bash : CLI구조이며, 처음 진입 장벽이 좀 높은편이고 사용할줄 알게되면 GUI를 익숙하게 사용할 수 있음
- Git GUI : Git 기능 중 일부만 지원하며, GUI로는 도저히 해결할 수 없는 문제들이 존재한다.
- 깃의 UI 외의 구조로는 3가지 구조가 있다
- 작업 디렉토리, 스테이징 영역, 깃 저장소가 있다

### 1-7. 브랜치
- 소스코드의 충돌을 막기 위한 개념으로 등장한 깃 기능이다.
- Branch 별로 작업이 가능하며, 이를 merge하여 최종본을 완성할 수 있다.

# 2. 깃허브
- 버전 관리를 위한 서버 저장소 및 프로젝트 개발을 위한 협업 관리 서비스
- 시스템 개발자와 운영을 담당하는 정보기술 전문가 사이 소통, 협업, 통합 및 자동화 지원
- 전세계 개발자가 함께 개발 지원
- 깃과 깃허브의 차이점은 아래에서 설명된다.
![image](https://user-images.githubusercontent.com/99636945/197134586-a7c77b4f-d2e2-4472-a525-94e5f3f184d6.png)
![image](https://user-images.githubusercontent.com/99636945/197134913-da09c8a6-410a-4781-a982-4fb62fe3d348.png)

# 3. 깃 명령어
### 3-1. 깃 설정
- Git Bash 실행 후 git에 관련된 설정을 몇 가지 해주어야 한다.
- 설정파일은 .gitconfig에 저장되며, local 수준이 global 수준보다 우선 순위가 높다.
- 명령어는 git config이며 그 뒤에 다른 옵션을 붙일 수 있다.
- git config --[global/local] [설정하려는 환경 변수] [설정값]
- 아래와 같이 사용자 설정 및 CRLF, 줄넘김 설정을 변경한다  
![image](https://user-images.githubusercontent.com/99636945/197136594-bde1251f-7b55-43a5-b44e-37759d4e55b5.png)
- 다음 명령어로는 깃에서의 편집기 설정을 바꿀 수 있다
![image](https://user-images.githubusercontent.com/99636945/197136815-5f4641ae-8710-4828-ba7d-d0e96eb2246e.png)
- 깃의 기본 브랜치 이름을 변경할 수도 있다.
![image](https://user-images.githubusercontent.com/99636945/197138814-7e24f45c-9ada-4a37-b858-0a799d537c2b.png)
- 전체 설정을 확인하려면 git config --list를 이용한다.
- 부분 설정값은 git config [보고자 하는 설정] 으로 확인한다.

### 3-1. 깃 저장소 생성/삭제
- 다른 설정들이 전부 마무리되면, git init으로 깃 저장소를 만든다.
- 디렉터리를 git repository로 만들어야 git으로 버전 관리가 가능하다
- git init [디렉터리 이름] 디렉터리 이름을 지정하면 그 디렉터리에 git 저장소를 생성한다.
- 저장소를 삭제하려면 리눅스의 rm -rf .git을 입력하면 강제로 삭제할 수 있다.
- 저장소가 아닌 설정을 삭제하려면 git config에서 --unset 옵션을 덧붙이면 된다
![image](https://user-images.githubusercontent.com/99636945/197138475-f9051cb3-bba2-4c9c-b0fb-ff2f3b527c1f.png)

### 3-2. 관리 파일, 파일 추가 및 커밋
- 파일의 상태는 두 가지로 나뉜다.
- Untracked : 관리 대상이 아닌 파일을 의미한다. git add로 추가하면 Tracked 파일이 된다.
- Tracked : git add로 추가된 관리될 수 있는 파일
![image](https://user-images.githubusercontent.com/99636945/197139260-30463348-6367-4e63-87d7-494b15812efd.png)
- 깃의 라이프 사이클을 보면 더 쉽게 이해할 수 있다.
![image](https://user-images.githubusercontent.com/99636945/197139546-ee2025d9-5918-49d7-9de5-207b3bbe716c.png)
- 파일이 Tracked 상태가 되기 전 까지는 Commit이 불가능하다.
- 그렇기에 파일을 생성하거나 수정하면, git add를 우선시 해야한다.
- add, commit 등 어떠한 동작을 해야 하는 지 모르겠다면, git status 명령을 사용해야 한다.
- 상태메시지는 아래 사진과 같다.  
![image](https://user-images.githubusercontent.com/99636945/197140326-315b7c58-bfcc-4d7e-a7c5-daabe9b9cf55.png)
![image](https://user-images.githubusercontent.com/99636945/197140560-a02daa45-63e9-4a6b-8012-1b11dea8cf7e.png)

### 3-3. 커밋 히스토리 확인
- git log로 확인한다. 
- 확인할 수 있는 내용은 Author 영역의 이름과 이메일 주소, 마지막 커밋 HEAD부터 모든 이력 로그, 커밋 메시지 등이 있다.
- --oneline, --graph 등의 옵션이 있지만 추후에 설명한다.

### 3-4. 파일의 생애주기 상세
- Tracked와 Untracked로 나뉘고 워킹디렉터리의 모든 파일이 이 주기를 가진다.
![image](https://user-images.githubusercontent.com/99636945/197141258-9f135fd2-e711-4376-8228-278cdb0c6621.png)
![image](https://user-images.githubusercontent.com/99636945/197141368-1b817ef0-08f6-437a-9df9-c3ef8fbb809d.png)
- 아래 그림으로 간략하게 알 수 있다.
![image](https://user-images.githubusercontent.com/99636945/197141638-cfd6598b-b3dd-499b-9686-585ade46ed82.png)

### 3-5. 깃 저장소 상태 정보
- git status로 확인하고 -s 옵션으로 간단하게 확인할 수 있다.
- -s 옵션은 --short와 동일하다.
- status 옵션으로 볼 수 있는 상태는 다음과 같다.  
![image](https://user-images.githubusercontent.com/99636945/197142774-903a1f9d-f48d-4cf8-96e5-b93afb9a52dd.png)
- 상태 변화는 다음과 같다  
![image](https://user-images.githubusercontent.com/99636945/197142857-5d7e73ae-e315-402c-9ce9-773875515941.png)
- 이후 Working Directory의 수정을 취소하려면 git restore 명령을 사용하면 된다.
- stage Area에 올린 것을 취소하려면 --staged 옵션을 덧붙인다.
![image](https://user-images.githubusercontent.com/99636945/197310586-dd0b13ea-7e54-4db7-9a5d-4d3d6bfa92e2.png)

### 3-6. 작업공간, Staging Area에 있는 파일 삭제
- git rm 명령어를 사용한다.
![image](https://user-images.githubusercontent.com/99636945/197310672-da902efd-e5c2-45ef-b6dc-3b38606bd6a7.png)
- --cached 옵션을 사용하면 작업 공간은 보존하고, staged Area에 있는 파일만 삭제한다.
![image](https://user-images.githubusercontent.com/99636945/197310666-069dd5ae-34a2-4810-ab18-14ae9c413c48.png)
- 강제 삭제 옵션은 -f를 사용한다.
- 강제 삭제 옵션을 사용해야 하는 경우는 아래 두 가지 사항으로 오류가 나는 경우이다.
![image](https://user-images.githubusercontent.com/99636945/197310745-c4b35159-84a2-4249-807f-861e7ab7134e.png)

# 4. 지역과 원격저장소 연동 기초
### 4-1. 지역에서 깃허브 저장소 클론(Clone)
- fork를 이용하여 원격 저장소를 내 깃허브 repository로 가져올 수 있다.
- 이후, fork로 연동된 저장소를 clone로 내 PC에 저장하면, Git Bash를 이용한 이력관리를 할 수 있다.
![image](https://user-images.githubusercontent.com/99636945/197310776-6c011226-90d7-4b4e-9881-f00725bef54e.png)
- 명령어는 git clone [저장소 url] 이다.
- 원격 저장소 별칭을 확인하려면 git remote를 사용한다. -v 옵션을 덧붙이면 주소도 같이 조회한다.

### 4-2. 깃허브 저장소 수정 후 풀(Pull) 또는 푸시(Push)
- 원격, 지역 간의 데이터 공유의 대략적인 구조는 다음과 같다.
![image](https://user-images.githubusercontent.com/99636945/197311010-f05fff92-64f2-4e96-b022-7becc6417358.png)
- git pull 명령어는 원격 저장소에서 변경사항이 발생할 경우, PC에 있는 깃 저장소로 변경사항을 내려받고 싶을 때 사용한다.
- git push 명령어는 지역 저장소(PC)에서의 변경 사항을 원격 Git Repository에 반영하고 싶을 때 사용한다.
- git push는 자신의 저장소가 아닌 경우, Write 권한이 주어져야 가능하다.

### 4-3. Pull Request
- fork된 상대의 저장소에 대한 변경사항을 Pull Request를 요청하여 병합을 요청하는 과정이다.
![image](https://user-images.githubusercontent.com/99636945/197312211-bb244dbe-0f28-4028-818d-70282ce5dbef.png)
- 저장소에 대한 쓰기 권한이 없을 경우 Request를 요청하여 상대가 확인한 후, 병합할 수 있다.

# 5. 브랜치
### 5-1. 브랜치에 대한 이해
- Branch는 나무 가지에서 유래한 기능이다.
- 개발 과정에서 각각 서로 다른 버전의 코드가 만들어질 수 있는 상황이 존재한다.
- 이때 여러 브랜치로 나누어 작업하고, 병합하여 유동적인 작업을 할 수 있다.
- 예시로는 동일한 소스코드를 어떤 사람은 버그를 수정하고, 어떤 사람은 새로운 기능을 만들어내는 경우이다.
- 각자의 독립적인 영역에서 마음대로 소스코드를 변경할 수 있다.
- 각각의 부른채는 다른 브랜치와 병합(Merge)함으로써 작업한 내용을 다시 병합할 수 있다.
![image](https://user-images.githubusercontent.com/99636945/197313795-ece08bbc-65cd-49de-885e-8c79cfd6051e.png)
![image](https://user-images.githubusercontent.com/99636945/197313955-cba035fb-e563-489e-8558-c48494beecca.png)

### 5-2. main 브랜치
- 저장소를 처음 생성하면, main이란 이름으로 브랜치를 생성한다.
- 원래는 master였지만, master/slave 개념을 IT업계에서 쓰지 않을것을 권장하기에, main이란 이름을 쓸 것을 권장하고 있다.
- 새로운 저장소에 새 파일을 추가하거나, 파일 내용을 변경하여 그 내용을 저장하는 것을 처리할 수 있다.
- 모든 작업은 main 브랜치에서 이루어진다.
- branch를 생성할 수도 있고, 다른 브랜치로의 이동도 가능하다.
- 브랜치 생성은 git [branch/switch -c/checkout -b] 등을 활용한다.
- 브랜치 이동은 git [switch/checkout] 을 사용한다.

### 5-3. 브랜치의 장점과 활용
- 하나의 큰 작업 흐름의 단위인 브랜치로 작업하게 된다.
- 기록을 중간중간 남기므로 문제 발생에 대해 원인을 찾거나 대책을 세우기 쉬워진다.
- 브랜치 이름에는 일반적으로 5개의 규칙이 있다.
- 항상 유지되어야 하는 main, develop 브랜치와 일정 기간만 유지되는 feature, release, hotfix 가 있다.
- 이중 main 브랜친느 언제든지 배포할 수 있는 버전을 만들어야 하는 브랜치이다.
- 그래서, 늘 안정적인 상태를 유지하는 것이 중요하다.
- Pull Request 또한 각 Branch 별로 요청할 수 있다.

### 5-4. 토픽 브랜치
- 통합 브랜치에서 생성되는 브랜치이다.
- 기능 추가 및 버그 수정 같은 단위 작업을 위한 브랜치이다.
- 토픽 브랜치에서 특정 작업이 완료되면, 다시 통합 브랜치에 병합한다.
![image](https://user-images.githubusercontent.com/99636945/197315188-01fe2efc-e83e-4b00-b8eb-011cd2b38b1c.png)

### 5-5. 브랜치 합병
- main branch에서 임의의 브랜치를 생성 후 그 아래에 또 다시 브랜치를 생성한다.
![image](https://user-images.githubusercontent.com/99636945/197315381-1891fa46-3b52-4438-8d0c-10cdc78149e3.png)
![image](https://user-images.githubusercontent.com/99636945/197315404-5ff5ed58-08c0-4a3f-b284-ab74a7f9aca1.png)
- 두 결과의 차이점은 feature2 브랜치에서 어디로 PR을 보냈느냐에 있다.

### 5-6. branch별로 나누어 볼 수 있는 정보
![image](https://user-images.githubusercontent.com/99636945/197315599-65d58d09-0fd7-4262-8758-52262749ef13.png)

### 5-7. 브랜치 명령어
- 저장소 목록 조회 : git branch
- 저장소 목록(원격 포함 전체목록) : git branch -a
- 생성만 : git branch <브랜치 이름> 또는 git switch <브랜치 이름>
- 생성 후 이동 : git checkout -b <브랜치 이름> 또는 git switch -c <브랜치 이름>
- 삭제 : git branch -d <브랜치 이름>
- 강제 삭제 : git branch -D <브랜치 이름>
- 저장소 이동 : git checkout branch-name 또는 git switch branch-name
- 이전 브랜치로 이동 : git checkout - 또는 git switch -
- 도움말 : git branch -h

### 5-8. HEAD 포인터 관련
![image](https://user-images.githubusercontent.com/99636945/197315722-9703b487-c2b4-470b-b9de-f0d256576330.png)
- 보통 git log나 git diff를 사용할 때 HEAD^나 HEAD~n을 사용하여 해당 커밋 정보만 가져오는 경우에 사용한다.

## 5-9. checkout의 다양한 디테일
- git checkout [커밋 ID]를 사용할 수도 있다.
![image](https://user-images.githubusercontent.com/99636945/197315792-65280e09-3487-4bb4-a5ca-14f7272807c1.png)
- detached HEAD를 사용하여 특정 커밋의 새로운 브랜치를 만들어 작업할때도
![image](https://user-images.githubusercontent.com/99636945/197315818-45718683-e3d3-498c-90e8-cf1777030873.png)
![image](https://user-images.githubusercontent.com/99636945/197315868-b310720b-8f68-4526-9c33-c531cff2b85f.png)
![image](https://user-images.githubusercontent.com/99636945/197315985-5a115a10-c798-49f1-9c79-503b1cddd09b.png)
![image](https://user-images.githubusercontent.com/99636945/197315991-30763a47-44a3-4d04-9e12-5a919d8ed42e.png)

### 5-10. Reset과 Checkout 비교
![image](https://user-images.githubusercontent.com/99636945/197316043-8608e1d5-3c6b-4312-9f1a-a661391b1e4b.png)

# 6. 파일 또는 커밋간의 차이를 보는 git diff
### 6-1. 개념
- Working directory와 Staging Area 사이의 차이를 보여준다.
- Staging 된 파일 상태 및 현재 수정중인 상태 비교
- 특정 파일을 지정하면 파일에 대한 차이를 알려준다.
- WD/SA간 차이를 비교할 수 있고, Commit, Branch 간의 차이도 비교 가능하다
![image](https://user-images.githubusercontent.com/99636945/197316290-5044cccf-c0dc-4c9b-9d63-b8cf30e90a69.png)

### 6-2. 명령어
- 수정 상태 비교(WD/SA) : git diff
- commit된 파일과 add된 파일 비교 : git diff --staged
- commit 간 상태 비교 : git diff [commit hash1] [commit hash2]
- commit 간 상태 비교(HEAD 포인터) : git diff HEAD HEAD^ 처럼 사용
- branch 간 상태 비교(HEAD 포인터) : git diff [branch1] [branch2]
- HEAD 포인터는 마지막 커밋 정보를 가리킨다.
- diff의 개요를 정리하면 다음과 같다.
![image](https://user-images.githubusercontent.com/99636945/197316378-2d8b4cce-5c4f-49d0-9c05-a83ddb3f150a.png)

### 6-3. 커밋 간의 이동
- HEAD의 개념을 이해해야 하는데, 위에서 전부 설명했다.
- 현재 브랜치를 가리키는 포인터이며, 마지막 커밋의 위치를 가리키는 것이다.
- 최소 1번이상 커밋해야 HEAD 포인터의 위치를 확인할 수 있다.
![image](https://user-images.githubusercontent.com/99636945/197316478-884dae84-dc2a-4c63-b182-3e6abba8d4e8.png)
- 몇 가지 추가 개념들이 존재한다.
![image](https://user-images.githubusercontent.com/99636945/197316563-19813ce8-6550-4cef-9f1e-0efdb8c80609.png)
- 명령어 예시는 git checkout [HEAD~/HEAD^] 등을 사용해서 이전 커밋으로 되돌아 갈 수 있다.
- 커밋 정보를 보려면 git show [커밋ID/head]를 사용하면 된다.


















