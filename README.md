<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fe5b4792-f609-4d69-ae04-6e8191d52ea7" />

## 1. 개요
- 기간 : 2024년 6월 ~ 2024년 8월
- 인원 : PM 1명, DESIGN 1명, FE(Android) 3명, BE(SpringBoot) 4명
- 역할 :
  - 백엔드 파트원
  - 사건/사고 게시글 구현
  - 댓글 구현
- 기술스택 : 
  - JAVA 17
  - SpringBoot 3.3.2
  - Build Tool Gradle - groovy
- 의존성 : Spring Web, Spring Data JPA, Lombok, MySql Driver, Spring Security

## 2. 개발 내용

<table>
  <tr>
    <td align="center" width="50%">
      <img width="1920" height="1348" alt="image" src="https://github.com/user-attachments/assets/86fd5c5e-723b-450f-a0e3-17cda55edf49" /><br/>
      <sub>내 근처 사건 사고 </sub>
    </td>
    <td align="center" width="50%">
      <img width="1454" height="816" alt="image" src="https://github.com/user-attachments/assets/849ebf3b-8b39-451d-8d53-eaf48ede83e1" />
      <sub>국내 사건 사고 </sub>
    </td>
  </tr>
</table>
<br/>

1. 내 근처 사건·사고
   - 사용자의 현재 위치 기준 1.5km 이내에서 발생한 실시간 사건·사고 제보 기능을 구현했습니다.
   - 유저가 직접 '확인했어요'와 '허위예요' 버튼을 통해 제보의 진위 여부를 판별하도록 설계했습니다.
   - 신고 수가 10개를 초과하는 부적절한 게시글은 시스템에서 자동으로 삭제되도록 처리했습니다.
   - 제보자가 직접 '상황 종료'를 설정하여 해당 사건이 해결되었음을 표시할 수 있습니다.
   - `@Query`를 활용해 근처 1.5km 이내 데이터를 상황 종료 여부, 최신순·인기순·거리순으로 정렬하여 사용자에게 최적화된 정보를 제공합니다.
2. 국내 사건·사고
   - 게시글의 '확인했어요' 수가 10개를 넘으면 중요 정보로 판단하여 국내 게시판으로 승격시킵니다.
   - 국내 사건·사고 목록은 정보의 과부하를 방지하기 위해 상위 10개의 핵심 게시글만 유지하도록 관리합니다.
   - 국내 게시판의 데이터는 사용자의 확인순 및 최신순을 기준으로 정렬하여 신뢰도와 실시간성을 확보합니다.

   
## 3. 설계
<table>
  <tr>
    <td align="center" width="50%">
      <img width="621" height="1015" alt="image" src="https://github.com/user-attachments/assets/7f18bdc2-51d1-4afa-86df-4b25741fff1d" />
      <sub>API 명세서</sub>
    </td>
    <td align="center" width="50%">
      <img width="1422" height="822" alt="image (3)" src="https://github.com/user-attachments/assets/16668d5d-b5dd-464c-8884-41b556066354" /><br/>
      <sub>ERD 다이어그램</sub>
    </td>
  </tr>
</table>
<br/>
