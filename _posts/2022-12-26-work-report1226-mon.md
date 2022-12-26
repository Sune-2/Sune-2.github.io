---
title: Work Report (22-12-26 Mon)
author: hyungsun
date: 2022-12-26 17:30:00 +0900
categories: [Report]
tags: [Report]
---

# 업무일지 (221226 Mon)

> 오늘 할 일
{: .prompt-tip }
  + [x] 업무 일지
  + [ ] 화면 설계서 - REST API, WBS 이미지, 화면 설계 추가
  + [ ] WBS - 프론트 및 백엔드 계획 세부화
  + [ ] 회원 시스템 개발
  + [ ] 게시판 개발
  + [ ] 예약시스템 개발

> 세부 사항
{: .prompt-info }
- 시스템 개발
   - 회원 시스템 현황

      ---
      + [x] JPA 방식 --> Spring Data JPA 방식으로 변경
      + [x] Dto와 @Builder를 사용
      + [x] Spring Security를 통하여 비밀번호 암호화 적용

      ![MemberService Test](/assets/img/screenshot/join.png)
      ![MemberService Test](/assets/img/screenshot/joinDb.png)
      + [ ] Login 시스템 구현

      ---

   - 게시판 현황

      ---
      + [x] Board Entity와 BoardDto, Bulider 사용
      + [x] Paging : 게시글 id 기준으로 내림차순 정렬 --> 최근 게시글이 앞페이지로

      ![MemberService Test](/assets/img/screenshot/boardList.png)
      ![MemberService Test](/assets/img/screenshot/boardList2.png)
      + [x] update, delete 구현
      + [x] 조회수 구현
      + [ ] 사용자에 따른 작성자 저장 --> Login 필요 (작성자 null인 상태)

      ![MemberService Test](/assets/img/screenshot/boardview.png)

      ---
   - 예약 시스템 현황

      ---
      - 캘린더 사용 고민중
      
      ---