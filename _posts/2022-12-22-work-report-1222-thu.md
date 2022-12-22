---
title: Work Report (22-12-22 Thu)
author: hyungsun
date: 2022-12-22 20:00:00 +0900
categories: [Report]
tags: [Report]
---

# 업무일지 (221222 Thu)

> 오늘 할 일
{: .prompt-tip }
  + [x] 업무 일지
  + [x] WBS(Work Breakdown Structure) 작성하기
  + [x] 주제 선정
  + [x] 화면 설계서 작성하기

> 세부 사항
{: .prompt-info }
- 시스템 개발
   - 회원 시스템

      ---

      MemberServiceTest
      ---
      ~~~java
      @Transactional
      @SpringBootTest
      @Slf4j
          class MemberServiceTest {

      @Autowired
      MemberService service;
        
      @Test
      void join() {
          Member member = new Member("test01", "1111", "가가가", "M", "20001201", 
                  "010-1111-1111", "test01@naver.com", "서울시");
          
          Member joinMember = service.join(member);
          
          assertThat(joinMember.getId()).isEqualTo(member.getId());
      }

      @Test
      void findByIdMember() {
          Member member = new Member("test02", "2222", "나나나", "M", "20001202", 
                  "010-2222-2222", "test02@naver.com", "인천시");	
          Member joinMember = service.join(member);
          
          Member findByIdMember = service.findByIdMember(joinMember.getId()).get();
          
          assertThat(findByIdMember.getId()).isEqualTo(member.getId());
      }
      
      @Test
      void findByUserIdMember() {
          Member member = new Member("test03", "3333", "다다다", "M", "20001203", 
                  "010-3333-3333", "test03@naver.com", "부산시");	
          Member joinMember = service.join(member);
          
          Member findByUserIdMember = service.findByUserIdMember(joinMember.getUserId()).get();
          
          assertThat(findByUserIdMember.getUserId()).isEqualTo(joinMember.getUserId());
      }
       
      @Test
      void findByUserNameMember() {
          Member member = new Member("test04", "4444", "라라라", "M", "20001204", 
                  "010-4444-4444", "test04@naver.com", "대전시");	
          Member savedMember = service.join(member);
          
          Member findByUserNameMember = service.findByUserNameMember(savedMember.getUserName()).get();
          
          assertThat(findByUserNameMember.getUserName()).isEqualTo(savedMember.getUserName());
      }
       
      @Test
      void findAllMembers() {
          List<Member> before = service.findAllMembers();
          Member member = new Member("test05", "5555", "마마마", "M", "20001205", 
                  "010-5555-5555", "test05@naver.com", "대구시");	
          service.join(member);
          
          List<Member> after = service.findAllMembers();
           
          assertThat(after.size()).isEqualTo(before.size()+1);
      }
        
      @Test
      void updateMember() {
          Member member = new Member("test06", "6666", "바바바", "M", "20001206", 
                  "010-6666-6666", "test06@naver.com", "춘천시");	
          Member savedMember = service.join(member);
          
          Member updateMember = new Member("test06", "66666", "바바바바", "M", "20011206", 
                  "010-6666-0000", "test06B@naver.com", "원주시");	
          service.updateMember(savedMember.getId(), updateMember);
          
          assertThat(service.findByIdMember(savedMember.getId()).get().getUserName())
              .isEqualTo(updateMember.getUserName());
      }
       
      @Test
      void authorityMember() {
          Member member = new Member("test07", "7777", "사사사", "M", "20001207", 
                  "010-7777-7777", "test07@naver.com", "파주시");	
          Member savedMember = service.join(member);
          
          service.authorityMember(savedMember.getId(), Grade.Manager);
          
          assertThat(service.findByIdMember(savedMember.getId()).get().getGrade()).isEqualTo(Grade.Manager);
      }
      }
	  ~~~
	  ---
	  ![MemberService Test](/assets/img/trouble/servicetest.png)

	  ---
	  ---
	  ![Join](/assets/img/trouble/join.png)

	  ---
      ---
	  ![Join H2](/assets/img/trouble/join2.png)

	  ---
