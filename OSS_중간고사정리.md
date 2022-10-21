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








