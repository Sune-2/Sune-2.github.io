---
title: Work Report (22-12-14 Wed)
author: hyungsun
date: 2022-12-14 09:30:00 +0900
categories: [Report]
tags: [Report]
---

# 업무일지 (221214 Wed)

> 오늘 할 일
{: .prompt-tip }
  + [x] 업무 일지
  + [ ] WBS(Work Breakdown Structure) 작성하기
  + [x] 주제 선정
  + [ ] 화면 설계서 작성하기

> 세부 사항
{: .prompt-info }
1. 업무 일지 작성
  + [x] 블로그 개설
  + [x] 업무 일지 작성
  + [ ] 트러블 슈팅

2. 화면 설계서 작성하기
  + [x] 서비스 개요
  + [ ] 유스케이스
  + [x] 시스템 구조, 사이트맵 구조
  + [x] 사이트맵 상세, 프로세스 정의
  + [ ] 디자인 시스템

3. 시스템 개발
   - 회원 시스템
      ~~~java
        @Getter @Setter @Entity
        public class Member {
          @Id
          @GeneratedValue(strategy = GenerationType.IDENTITY)
          private Long id;
          @Column(name = "userid")
          private String userId;
          @Column(name = "password")
          private String password;
          @Column(name = "username")
          private String userName;
          @Column(name = "birthday")
          private String birthday;
          @Column(name = "phone")
          private String phone;
          @Column(name = "email")
          private String email;
          @Column(name = "address")
          private String address;
          @Column(name = "grade")
          @Enumerated(EnumType.STRING)
          private Grade grade = Grade.General;
        
          public Member(String userId, String password, String userName, String birthday,
                    String phone, String email,String address) {
            this.userId = userId;
            this.password = password;
            this.userName = userName;
            this.birthday = birthday;
            this.phone = phone;
            this.email = email;
            this.address = address;
          }
        }
      ~~~
      ---
      ~~~java
        public interface MemberRepository {
        // 회원 가입
        Member save(Member member);
          
        // 회원 검색
        Optional<Member> findById(Long id);
        Optional<Member> findByUserId(String userId);
        Optional<Member> findByUserName(String name);
          
        // 회원 전체 검색
        List<Member> findAll();
          
        // 회원 정보 수정
        void update(Long id, Member member);
          
        // 회원 등급 변경
        void authority(Long id, Grade grade);
        }
      ~~~
      ---
      ~~~java
      @Repository
      public class MemberJpaRepository implements MemberRepository {

        private final EntityManager em;
        
        public MemberJpaRepository(EntityManager em) {
          this.em = em;
        }
        
        @Override
        public Member save(Member member) {
          em.persist(member);
          return member;
        }

        @Override
        public Optional<Member> findById(Long id) {
          Member member = em.find(Member.class, id);
          return Optional.ofNullable(member);
        }

        @Override
        public Optional<Member> findByUserId(String userId) {
          List<Member> member = em.createQuery("select m from Member m where m.userId = :userId", Member.class)
              .setParameter("userId", userId).getResultList();
          return member.stream().findAny();
        }
        
        @Override
        public Optional<Member> findByUserName(String userName) {
          List<Member> member = em.createQuery("select m from Member m where m.userName = :userName", Member.class)
              .setParameter("userName", userName).getResultList();
          return member.stream().findAny();
        }

        @Override
        public List<Member> findAll() {
          return em.createQuery("select m from Member m", Member.class).getResultList();
        }

        @Override
        public void update(Long id, Member member) {
          em.createQuery("update Member m set m.password = :password, m.userName = :userName,"
                  + "m.phone = :phone, m.email = :email, m.address = :address where m.id = :id")
                .setParameter("password", member.getPassword())
                .setParameter("userName", member.getUserName())
                .setParameter("phone", member.getPhone())
                .setParameter("email", member.getEmail())
                .setParameter("address", member.getAddress())
                .setParameter("id", id)
                .executeUpdate();
          
          em.flush();
          em.clear();	
        }

        @Override
        public void authority(Long id, Grade grade) {
          em.createQuery("update Member m set m.grade = :grade")
            .setParameter("grade", grade)
            .executeUpdate();
          
          em.flush();
          em.clear();	
        }
      }
      ~~~