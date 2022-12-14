# 1. Stash
- 놓다, 남겨두다, 감추다, 안전한 곳에 숨겨두다라는 의미를 지님
- 커밋 필요 없이 변경사항을 숨기거나 비밀리에 저장할 수 있음
- Working Directory, Stage Area의 영역을 스택에 저장한다.
- 이후 내용은 Git Repository의 가장 마지막 커밋에 저장된 내용으로 반영된다.
- 저장 내용은 작업 디렉터리 내용과 스테이지 내용이다.  
![image](https://user-images.githubusercontent.com/99636945/205543810-e5c8e824-4fe0-45ba-91af-98735d4285e4.png)

### 1-1. 필요성
- 작업 디렉터리가 정리되고, git이 추적한 모든 파일이 스택에 저장됨
- 그후 자유롭게 변경 및 커밋, 분기 전환과 다른 Git 작업을 수행할 수 있다.
![image](https://user-images.githubusercontent.com/99636945/205544248-dabe69b5-68a4-4a81-8406-e1f517e43d5c.png)
- stash 내용을 가져가 사용할 때는 기본으로 작업 디렉터리 내용만 다시 복사해 활용
- 스테이지 영역도 복사하려면 옵션을 사용해야 한다.(apply --index)
![image](https://user-images.githubusercontent.com/99636945/205544329-0fb28704-5889-4bbd-9714-77740aacdeef.png)

### 1-2. Stash 주요 옵션 및 명령어
![image](https://user-images.githubusercontent.com/99636945/205544377-7861e3f1-4181-4228-84e6-ac7954925d2c.png)
![image](https://user-images.githubusercontent.com/99636945/205545445-7e8f79f6-cf26-4e0b-b258-7f7b6c72656e.png)
![image](https://user-images.githubusercontent.com/99636945/205545464-5f3356b3-3c8d-42e5-9614-f939f522ed48.png)

### 1-3. Untracked 파일 삭제
- git clean 명령을 사용한다.
- 강제로 삭제하려면 -f 옵션을 덧붙인다.

### 1-4. Stash에서 분기 만들기
![image](https://user-images.githubusercontent.com/99636945/205545781-f664eaad-14bf-4076-909f-08c003a115f9.png)


# 2. 브랜치 병합
### 2-1. 수동 병합
- 하나씩 직접 비교하는 방식임
- 양쪽 파일을 일일이 비교하며 바뀐점을 찾아서 적용해야함.
- 오류없이 코드를 병합하는 것은 간단하지 않고, 사람의 기억력에 대한 한계점이 명확함


### 2-2. 깃으로 자동 병합
- 복잡한 파일을 좀 더 간편하게 병합할 수 있음
- 모든 코드를 완벽하게 병합하는 것은 아니며, 이로 인해 발생하는 현상을 충돌이라고함
- 브랜치를 기준으로 병합하며, 같은 저장소 내 서로 독립적인 작업을 분리한 영역이다.
- 각각의 브랜치에서 수정된 사항을 하나의 브랜치로 병합한다. 이때 병합하려는 브랜치는 같은 로컬 저장소에 있어야 한다.

### 2-3. 병합 방식
- 병합에 있어서 상대적인 기준을 판별하는 알고리즘이 존재한다.
- Fast-Forward와, 3-way 병합 방식을 제공한다.
![image](https://user-images.githubusercontent.com/99636945/206076712-8c287c5a-dabd-41bb-99b5-2c97140e88a7.png)

### 2-3. Fast-Forward 병합 적용
- 병합 메시지에 Fast-Forward 방식으로 적용 되었다고 출력된다.
- 병합 원리는 다음과 같다  
![image](https://user-images.githubusercontent.com/99636945/206076918-996c2615-6fde-4d67-9e78-7fa7f38e4e39.png)

- git log를 찍어보면 작업한 브랜치의 시작 커밋을 원본 브랜치 이후의 커밋으로 가리키는 것을 확인할 수 있다.
 <img width="315" alt="ㅇ" src="https://user-images.githubusercontent.com/101856066/200575247-160b9ddc-48e9-49d1-ad7e-76e45a50c0b4.png">
 <img width="253" alt="ㅈ" src="https://user-images.githubusercontent.com/101856066/200575690-07804d3f-8c07-41d4-a50a-a089c7d22d06.png">
- 이를 통해 Fast-Forward 병합은 병합할 하나의 브랜치 파일을 기준 브랜치로 복사하여 수정된 파일을 원본에 그대로 적용한 것과 같다는 점을 알 수 있다.

### 2-4. 3-way 병합
- 좀 더 복잡한 병합을 처리할 수 있는 방법.
- 여러 개발자와 협업으로 작업하는 경우 대부분 3-way 병합을 사용.
- 원리는 다음과 같다
![image](https://user-images.githubusercontent.com/99636945/206077049-9cf5d86a-d171-4a31-9066-119c3cf71dd3.png)
![image](https://user-images.githubusercontent.com/99636945/206077163-0a6a9bb1-329e-45bc-bd71-ad650a0e8805.png)  
- 여기서 -m으로 메세지를 주지 않으면, 병합 메시지를 입력할 기본 편집기를 실행한다.

# 3. 충돌
### 3-1. 충돌이 생기는 상황
- 여러 사람과 개발 작업을 하다 보면 예상외로 충돌이 자주 발생.
- 대부분의 충돌 원인은 같은 위치의 코드를 동시에 수정했기 때문.
- 파일을 수정할 때 여러 개발자가 서로 다른 위치를 수정했다면 깃에서 서로 다른 위치의 소스를 자동으로 병합하기 때문에 문제 없음.
- 하지만 파일에서 동일한 위치에 두 명 이상이 서로 다르게 수정했다면 충돌이 발생.
![image](https://user-images.githubusercontent.com/99636945/206077707-ebaedbbe-544d-46c0-acb3-5c64d947c9d6.png)

### 3-2. 병합 사례 및 차이점
![image](https://user-images.githubusercontent.com/99636945/206077881-a16c622a-5077-4cf6-a9ba-c4820679a3ce.png)
![image](https://user-images.githubusercontent.com/99636945/206077943-bcea9e7a-f2b5-4116-ad03-9c0e9bb6a076.png)
![image](https://user-images.githubusercontent.com/99636945/206078228-27e6d4f2-8b3a-4310-bc76-e3c1a1b9241e.png)

### 3-3. 주의점
- merge 전 Stage 영역에 작업중인 파일이 없는지 꼭 확인할 것
![image](https://user-images.githubusercontent.com/99636945/206078645-50283148-8804-46d3-89ad-f5546e5a0b2d.png)

### 3-4. Merge의 다양한 옵션
- Fast Forward 여부와 관련된 옵션은 다음과 같다  
![image](https://user-images.githubusercontent.com/99636945/206079293-cac6238a-6320-438d-a621-afac3f1df7a4.png)
![image](https://user-images.githubusercontent.com/99636945/206095295-4fae4768-ad7f-4aca-9f24-bebdd9cb63aa.png)
- --no-ff 옵션 사용 시 무조건 3-way merge를 한다
![image](https://user-images.githubusercontent.com/99636945/206095433-55113061-bbc8-4791-981c-1a4d36f20708.png)
- --squash를 사용하면 commit 이력, merge된 브랜치 이력을 남기지 않음
![image](https://user-images.githubusercontent.com/99636945/206095509-7e447519-4eb7-4a70-8a0c-c4ae37840f00.png)

# 4. Rebase
- 브랜치를 합치는 방식에는 병합과 리베이스가 있음
- 커밋 순서를 재배열하는 것이 리베이스임

### 4-1. 베이스
- 모든 브랜치는 뿌리가 있음(master 예외)
- 특정 커밋은 브랜치가 파생된 기준이 됨
- 베이스란, 공통 조상 커밋이라고도 하는데 해당 커밋을 기준으로 커밋이 여러갈래로 갈라지는 경우를 의미함.

### 4-2. 베이스 변경
- 베이스 앞에 re라는 의미가 붙음
- 베이스 커밋을 변경하는 것을 말함
- 이를 통해 병합을 하면서 일어나는 공통 조상 커밋 찾기 과정 등을 생략할 수 있음
- 여러갈래의 커밋 진행을 일원화 하면서 쉽게 파악할 수 있음

### 4-3. 리베이스 vs 병합
- 병합은 파생된 두 브랜치를 합치는 과정
- 공통 조상 커밋을 찾고 3-way 병합을 진행해야 함
- 리베이스는 브랜치를 서로 비교하지 않고 순차적으로 병합을 진행함
- 가장 큰 차이점은 3-way 병합은 병합 커밋이 존재하지만 리베이스는 병합 커밋이 없음
- 브랜치의 마지막을 가리키는 커밋 위치가 다르다는 점도 존재함

### 4-4. Rebase 원리
![image](https://user-images.githubusercontent.com/99636945/206096726-fa29b569-b109-4876-9900-3e6656810d8e.png)
![image](https://user-images.githubusercontent.com/99636945/206097112-aab8bde5-5947-4360-9bd9-306b1b7dfb7d.png)

### 4-5. 충돌과 해결
- 리베이스 역시 병합 과정에서 충돌이 발생할 수 있음
- 사용자가 직접 수동으로 충돌을 해결해야 함
![image](https://user-images.githubusercontent.com/99636945/206097516-94c34f3a-d0bc-4836-9651-07132c5e8e20.png)

### 4-6. 3-way 및 fast-forward와 rebase 비교
![image](https://user-images.githubusercontent.com/99636945/206097673-7551338d-7d16-4b6c-92e4-b914fcb1bc2f.png)
![image](https://user-images.githubusercontent.com/99636945/206097783-8fa87a56-ae56-4a67-a302-d1da4b91b46f.png)

### 4-7. 리베이스 절차
- main 브랜치에서 다른 브랜치로 이동 후 rebase main을 실행
- main으로 되돌아와서 merge를 실행해야 rebase 결과 후 커밋이력이 제대로 반영됨
![image](https://user-images.githubusercontent.com/99636945/206097960-79a52412-3bbb-461a-b089-6c5727bbe06a.png)
- 리베이스 방법에는 여러가지가 있다. 예시는 다음과 같다
![image](https://user-images.githubusercontent.com/99636945/206098238-5b3e6e6c-83a7-4dbc-8192-824c4e138d36.png)

# 5. 커밋 메시지 수정
- 마지막 커밋은 --amend 옵션으로 수정할 수 있다.
- 리베이스는 커밋 위치를 재조정하여 병합과 유사한 효과를 보임(실제 병합은 아님)
- 여러 커밋을 한 커밋으로 묶을 수도 있음 이때는 -i 옵션을 사용하면 됨
![image](https://user-images.githubusercontent.com/99636945/206098496-882d5491-302c-4fba-9dbf-955d160edc34.png)
![image](https://user-images.githubusercontent.com/99636945/206098529-957ef7d0-7d04-4d78-b2a4-f9686e2ff5f6.png)
- rebase -i를 사용하면, 대화식 인터페이스를 보여주는데 사용하는 명령어는 다음과 같다
![image](https://user-images.githubusercontent.com/99636945/206098616-94062ad5-3650-42ef-9925-3a48f5b7d509.png)

# 6. Reset
- 깃을 이용하여 버전을 관리하는 목적은 만일의 사태를 대비하기 위해서임
- 개발자는 코드를 단계별로 발전 시키면서 실수를 최소화하고자 노력해야함
- 아무리 주의해서 프로그래밍해도 오류가 생길수 있음
- 억지로 문제를 해결하는 것 보다는 작업을 포기하고 다시 시작하는 것이 더 빠를 수 있음
- 깃으로는 원하는 시점으로 언제든지 전체 코드를 되돌릴 수 있음
- 리셋은 커밋을 기준으로 이전 코드로 되돌리는 방법으로, 기록된 커밋을 취소함
- 커밋을 취소하는 만큼 리셋 시 신중해야함

### 6-1. Git의 4가지 영역
![image](https://user-images.githubusercontent.com/99636945/206100801-859ef1c8-ff98-47ec-8220-bc2e13ca2a9b.png)
- 커밋을 수행하고 나면 커밋 이력은 Repository에만 남아있음
![image](https://user-images.githubusercontent.com/99636945/206101002-d4e1684e-375b-410c-a242-6852825abc5b.png)

### 6-2. 복귀 시점
- 이전 코드로 복귀하려면 복귀 시점을 알려줘야 함
- log 명령어로 커밋 해시값을 확인 후 복귀하고자 하는 커밋의 해시값을 넣어 주면 됨  

### 6-3. reset 명령어
- 지정된 커밋 코드로 되돌아감
- 형식은 git reset [옵션] [커밋ID]이다.
- 옵션에는 아래 세 가지가 존재함.
- soft : 스테이지 영역을 포함한 상태로 복원
- mixed : 기본은 mixed임.
- hard : 실제 파일이 삭제된 이전 상태로 복원

### 6-4. 옵션 간 차이점 및 동작
![image](https://user-images.githubusercontent.com/99636945/206101134-e1094f22-06dd-44ee-8375-b9f8b3dfbdbe.png)
![image](https://user-images.githubusercontent.com/99636945/206101315-9329630f-5d42-4bdb-9cc9-89c1f17b9e33.png)
![image](https://user-images.githubusercontent.com/99636945/206101344-fb57e42f-091d-478f-ab85-47c400c5422a.png)
![image](https://user-images.githubusercontent.com/99636945/206101372-6b73dfde-ce81-45b1-9006-907a9e338084.png)
![image](https://user-images.githubusercontent.com/99636945/206101712-9cfb47d4-bb75-4a9d-988c-6f9f1798eec7.png)

# 7. Revert
- 공개 커밋을 되돌리기 위해서 하는 작업
- 커밋 정보 삭제 여부에 차이가 있음
- 리버트는 기존 커밋을 남겨 두고 취소에 대한 새로운 커밋을 생성함
- 취소 커밋 생성할 때에는 revert 명령어 사용
![image](https://user-images.githubusercontent.com/99636945/206101990-c0810e90-eb69-4108-af04-b3c2e7092718.png)

### 7-1. 리버트 지정
- 리버트는 한 번에 커밋 하나만 취소 가능
- 범위 지정 연산자를 사용하여 여러 커밋을 revert 할 수 있음
- 사용 예시는 git revert CommitID .. CommitID와 같이 사용
![image](https://user-images.githubusercontent.com/99636945/206102474-54a14e65-d318-4d27-9e2f-61b7f31d9679.png)

### 7-2. Revert 동작 및 결과
![image](https://user-images.githubusercontent.com/99636945/206102548-c0d53337-03e5-4e22-9f11-17191cdce871.png)
![image](https://user-images.githubusercontent.com/99636945/206102584-f68d11f0-a187-45eb-88ca-826d01833d91.png)

### 7-3. Reset 와 Revet, Checkout 비교
![image](https://user-images.githubusercontent.com/99636945/206102753-8ae63236-d529-46f4-bee0-5f390ef6a5ff.png)
![image](https://user-images.githubusercontent.com/99636945/206102828-fc439060-25bc-475d-a881-7ed037b2f8fd.png)







