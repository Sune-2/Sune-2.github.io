---
title: Work Report (23-01-07 Sat)
author: hyungsun
date: 2023-01-07 21:00:00 +0900
categories: [Report]
tags: [Report]
---

# 업무일지 (230107 Sat)

> 오늘 할 일
{: .prompt-tip }
  + [x] 업무 일지
  + [ ] 발표 자료 수정
    - [ ] Project명 정하기
    - [x] 개발 환경 세분화
    - [ ] 핵심 기능 - 목차, View 내용, 설명 추가
    - [ ] 트러블 슈팅 - 가독성 생각
    - [ ] 소감 
  + [x] 회원 시스템 개발
  + [x] 게시판 개발
  + [x] 예약시스템 개발

> 세부 사항
{: .prompt-info }
- 시스템 개발
   - 회원 시스템 현황

      ---
      + [x] Join 시스템 구현
      + [x] Login 시스템 구현
      + [x] Member Modify 시스템 구현
      + [ ] Member Role 구현 - 추가 진행 예정

      ---

   - 게시판 현황

      ---
      + [x] Board List/View 구현
      + [x] Board Write 구현
      + [x] Board Update/Delete 구현
      + [x] Board Search 구현
      + [ ] 게시판 구분(공지사항/리뷰) - 추가 진행 예정

      ---
   - 예약 시스템 현황

      ---
      + [x] Calendar 구현 - FullCalendar 이용
      + [x] Reservate 구현
      + [x] Calendar와 DB 연동
      + [x] Calendar 예약 여부 회원/비회원 구분
      + [x] Calendar 예약 상세 페이지

      ---
      아이디(test)로 로그인<br>
      ![calendar](/assets/img/screenshot/230107-calendar1.png)

      ---
      FullCalendar의 eventClick Handler 수정<br>
      ![calendar5](/assets/img/screenshot/230107-calendar5.png)

      "예약 완료" 이벤트 클릭 시 - alert() 이용하여 경고<br>
      ![calendar2](/assets/img/screenshot/230107-calendar2.png)

      ---
      "사용자 이름" 이벤트 클릭 시 - /calendar/check/{해당 날짜} 로 이동<br>
      ![calendar3](/assets/img/screenshot/230107-calendar3.png)
      ![calendar4](/assets/img/screenshot/230107-calendar4.png)
      ![calendar6](/assets/img/screenshot/230107-calendar6.png)

      ---
      + [ ] Calender 예약 취소 - 추가 진행 예정

      ---

> 트러블 슈팅
{: .prompt-danger }
1. DB에서 userId로 예약 정보를 가져오는 쿼리문 작성<br>--> 예약이 2개 이상인 경우 여러개의 결과가 나와 오류 발생
![calendar-error1](/assets/img/screenshot/230107-error1.png)<br>
![calendar-error2](/assets/img/screenshot/230107-error2.png)

2. reservateDate도 where문의 조건으로 사용하는 쿼리문으로 수정<br> --> 파라미터 date[2023-01-12]를 DB의 reservateDate와 비교 실패
![calendar-error3](/assets/img/screenshot/230107-error3.png)
![calendar-error4](/assets/img/screenshot/230107-error4.png)

3. 쿼리문이 잘못되었나 H2 DB에서 실행<br>--> 정상적으로 작동
![calendar-error5](/assets/img/screenshot/230107-error5.png)

4. 들어온 데이터가 String 이므로 이것을 Date로 변환하기로 함<br> --> DB에서 먼저 PARSEDATETIME 실행되도록 함
![calendar-error6](/assets/img/screenshot/230107-error6.png)

5. PARSEDATETIME을 query문안에 넣기<br> --> log 찍어보며 값이 어떻게 query문에 들어가는지 확인<br>
--> 파라미터를 StringTemplate를 통하여 포맷 변환 후 where문 안에 넣어 문제 해결
![calendar-error7](/assets/img/screenshot/230107-error7.png)

> 수정해야 할 것
{: .prompt-warning }
- 같은 날에 같은 사용자가 예약을 두 번 할 수 없도록 수정
   