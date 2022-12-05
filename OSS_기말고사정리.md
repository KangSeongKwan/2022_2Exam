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
