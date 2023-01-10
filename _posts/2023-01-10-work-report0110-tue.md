---
title: Work Report (23-01-10 Tue)
author: hyungsun
date: 2023-01-10 17:00:00 +0900
categories: [Report]
tags: [Report]
---

# 업무일지 (230110 Tue)

> 오늘 할 일
{: .prompt-tip }
  + [x] 업무 일지
  + [x] 발표 자료 수정 - 추후 세부 수정
  + [x] 회원 시스템 개발
  + [x] 게시판 개발
  + [x] 예약시스템 개발
  + [ ] Test - 진행중

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
      + [x] Board File Upload 구현

      ![fileupload1](/assets/img/screenshot/230110/board-fileupload1.png)
      ![fileupload2](/assets/img/screenshot/230110/board-fileupload2.png)
      + [ ] 게시판 구분(공지사항/리뷰) - 추가 진행 예정

      ---
   - 예약 시스템 현황

      ---
      + [x] Calendar 구현 - FullCalendar 이용
      + [x] Reservate 구현
      + [x] Calendar와 DB 연동
      + [x] Calendar 예약 여부 회원/비회원 구분
      + [x] Calendar 예약 상세 페이지
      + [x] Calender 예약 취소

   - 테스트 현황

      ---
      + [ ] Board Repository Test
      + [ ] Board Service Test
      + [x] Member Repository Test

      ![memberRepository Test](/assets/img/screenshot/230110/memberRepositoryTest.png)
      + [x] Member Service Test

      ![memberService Test](/assets/img/screenshot/230110/memberServiceTest.png)
      + [x] Reservate Repository Test

      ![reservateRepository Test](/assets/img/screenshot/230110/petRepository-test.png)
      + [x] Reservate Service Test

      ![petService Test](/assets/img/screenshot/230110/petService-test.png)

> 트러블 슈팅
{: .prompt-danger }
1. 이미지를 첨부 시, 사진 파일이 깨져서 나옴<br> --> 이미지 파일 경로는 제대로 입력되어있음
![fileupload Error1](/assets/img/screenshot/230110/fileupload-1.png)

2. 이클립스의 프로젝트를 refresh하면 그 후 이미지 보임<br> --> 이클립스의 파일 경로와 톰캣 서버의 배포 경로가 달라서 이미지가 보이지 않는 에러

3. 이클립스의 환경설정 변경<br> --> Window → Preferences → General → Workspace 의 Refresh using native hooks or polling 체크
![fileupload Error3](/assets/img/screenshot/230110/fileupload-3.png)

4. 이클립스의 환경설정 변경<br> --> Window → Preferences → General → Workspace -> Save automatically before manual build 체크
![fileupload Error4](/assets/img/screenshot/230110/fileupload-4.png)

5. 정상적으로 작동되기는 하나 이클립스가 파일을 불러오는 시간이 조금 걸리는 듯
![fileupload Error2](/assets/img/screenshot/230110/fileupload-2.png)
6. 나중에 이미지 파일을 별도의 디렉토리에 저장하여 불러오는 방법을 시도해볼 것 

   

   
   