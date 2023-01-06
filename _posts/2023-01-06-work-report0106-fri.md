---
title: Work Report (23-01-06 Fri)
author: hyungsun
date: 2023-01-06 17:30:00 +0900
categories: [Report]
tags: [Report]
---

# 업무일지 (230106 Fri)

> 오늘 할 일
{: .prompt-tip }
  + [x] 업무 일지
  + [x] 발표 자료 준비 - 점차 수정
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

      ---
      Controller의 JSON 생성을 Authentication 객체를 통하여 구분<br>

      Authentication 객체의 이름과 DB에 저장된 사용자의 이름을 비교하여 JSON 생성
      ![calendar controller](/assets/img/screenshot/calendar-auth3.png)

      ---
      로그인 X<br>
      예약 상황이 "예약 완료" 라고 보임
      ![calendar auth2](/assets/img/screenshot/calendar-auth2.png)

      ---
      로그인 O - 아이디(test)로 로그인<br>
      자신의 이름으로 예약된 것만 보임
      ![calendar auth1](/assets/img/screenshot/calendar-auth1.png)

      + [ ] Calendar 예약 상세 페이지 - 추가 진행 예정

      ---
   
   