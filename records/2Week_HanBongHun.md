## Title: [2Week] 한봉훈

### 미션 요구사항 분석 & 체크리스트

---
#### 필수 미션 - 호감표시 할 때 예외처리 케이스 3가지 처리  


- **체크 리스트**  
  - [x] 한명의 인스타 회원이 다른 인스타 회원에게 중복으로 호감표시 할 때 rq.historyBack
  - [x] 한명의 인스타 회원이 10명보다 많은 인원을 호감상대로 등록할 때 rq.historyBack
  - [x] 기존에 호감을 표시한 회원을 다른 유형으로 호감표시 할 때 성공으로 처리 후 메세지 표시 
#### 선택 미션 - 네이버 로그인
 - **체크리스트**
   - [x] 네이버로 로그인 했을 때 username이 NAVER_{id} 형태로 Member로 등록되는가
   
### 2주차 미션 요약


---

**[접근 방법]**
#### 중복으로 호감 표시 예외처리  
현재 로그인한 사용자가 호감을 표시한 LikeablePerson목록을 List에 저장
List를 돌면서 현재 호감을 등록하려는 대상의 username과 list요소 username을 비교
username이 서로 같은 경우 attractiveTypeCode를 비교하여 같으면 RsData에 실패 코드를 담아 리턴

#### 10명 이상의 호감 인원 등록 예외처리 
호감 등록 전에 현재 로그인한 사용자가 몇명의 LikeablePerson을 등록했는지 확인 후 10명이면 RsData에 실패 코드 담아 리턴 

#### 기존에 호감을 표시한 회원을 다른 유형으로 호감표시할 때 성공 처리 
중복으로 호감 표시 예외처리와 같은 방식으로 username이 같은 것을 확인한 후 attractiveTypeCode가 다르면 RsData에 성공 코드 담아 리턴 

#### 네이버 로그인 
네이버 로그인의 경우 로그인시 OAuth2User의 name이 json형태로 저장됨 
따라서 해당 문자열을 적절히 split과 replace하는 과정을 거쳐 id부분에 해당하는 값만을 얻어와 Member username값 할당 

**[특이사항]**
#### 후기
호감을 표시한 목록 중에서 username과 attractiveTypeCode를 확인하기 위한 반복문을 사용하는데 JPA에서 해당 쿼리를 직접 작성하는 방법이 있을 거 같다 

