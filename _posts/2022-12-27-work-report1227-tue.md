---
title: Work Report (22-12-27 Tue)
author: hyungsun
date: 2022-12-27 20:00:00 +0900
categories: [Report]
tags: [Report]
---

# 업무일지 (221227 Tue)

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
      + [ ] Join 시스템 구현 - Validation을 이용하여 제약조건 및 유효성 검증
         - th:object와 th:value 사용 시 binding을 제대로 하지 못하고 있음 - 수정중
         - gender의 radio button에 유효성 검사 오류 - 수정중
      + [ ] Login 시스템 구현 - Spring Security 이용하여 진행중
      + [ ] Member Modify 시스템 구현

      ---

   - 게시판 현황

      ---
      + [x] Board List 구현 - paging 이용
      + [ ] Board Write 구현
         - 사용자에 따른 작성자 저장 --> Login 필요 (작성자 null인 상태)
      + [x] Board Update 구현
      + [x] Board Delete 구현

      ---
   - 예약 시스템 현황

      ---
      + [ ] Calendar 시스템 구현 - 진행중
      
      ---