---
title: Work Report (23-01-05 Thu)
author: hyungsun
date: 2023-01-05 17:30:00 +0900
categories: [Report]
tags: [Report]
---

# 업무일지 (230105 Thu)

> 오늘 할 일
{: .prompt-tip }
  + [x] 업무 일지
  + [ ] 발표 자료 준비
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
      ![Calendar-DB](/assets/img/trouble/calendar-DB.png)
      ![Calendar-DB-script](/assets/img/trouble/calendar-DB-script.png)
      + [ ] Calendar 예약 여부 회원/비회원 구분 - 추가 진행예정

      ---

> 트러블 발생
{: .prompt-warning }
- Calendar와 DB 연동 중 json 값이 넘어가지않음
   1. Controller에서 Gson 라이브러리를 이용하여 json 생성
      - implementation 'com.google.code.gson:gson:2.9.0'
   ![hsonerror-2](/assets/img/trouble/jsonerror-2.png)

   2. Eclipse Console 창에 뜨는 jsonArr 값
   ![jsonerror-1](/assets/img/trouble/jsonerror-1.png)

   3. ResponseBody를 통하여 view에서 받은 json 값

   ![jsonerror-3](/assets/img/trouble/jsonerror-3.png)

> 트러블 슈팅
{: .prompt-danger }
- 원인 : JSONArray로 반환하였는데 이것을 넘길 때 json으로 인식하지 못하여 {"empty":false} 로 나타남
   1. Gson 라이브러리 대신 json-simple 라이브러리 사용
      + implementation group: 'com.googlecode.json-simple', name: 'json-simple', version: '1.1.1'
   2. Controller 수정 - 원래 계획대로 model을 통하여 넘김

   ![jsonerror-4](/assets/img/trouble/jsonerror-4.png)

   
   