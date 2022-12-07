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






