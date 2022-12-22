---
title: Work Report (22-12-15 Thu)
author: hyungsun
date: 2022-12-15 18:00:00 +0900
categories: [Report]
tags: [Report]
---

# 업무일지 (221215 Thu)

> 오늘 할 일
{: .prompt-tip }
  + [x] 업무 일지
  + [ ] WBS(Work Breakdown Structure) 작성하기
  + [x] 주제 선정
  + [x] 화면 설계서 작성하기

> 세부 사항
{: .prompt-info }
- 시스템 개발
   - 회원 시스템 - Member 도메인에 gender(성별) 추가
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
          @Column(name = "gender")
          private String gender;
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
        
          public Member(String userId, String password, String userName, String gender
	        String birthday, String phone, String email,String address) {
            this.userId = userId;
            this.password = password;
            this.userName = userName;
            this.gender = gender;
            this.birthday = birthday;
            this.phone = phone;
            this.email = email;
            this.address = address;
          }
        }
      ~~~
      ---
	  MemberJpaRepository Test

	  ---
      ~~~java

        @Transactional
        @SpringBootTest
        @Slf4j
        class MemberJpaRepositoryTest {

		@Autowired
		MemberJpaRepository repository;
	
		@Test
		void save() {
			Member member = new Member("test01", "1111", "가가가", "M", "20001201", 
					"010-1111-1111", "test01@naver.com", "서울시");
			
			Member savedMember = repository.save(member);
			
			assertThat(savedMember.getId()).isEqualTo(member.getId());
		}
		
		@Test
		void findById() {
			Member member = new Member("test02", "2222", "나나나", "M", "20001202", 
					"010-2222-2222", "test02@naver.com", "인천시");	
			Member savedMember = repository.save(member);
			
			Member findByIdMember = repository.findById(savedMember.getId()).get();
			
			assertThat(findByIdMember.getId()).isEqualTo(savedMember.getId());
			assertThat(findByIdMember.getEmail()).isEqualTo(savedMember.getEmail());
		}
		
		@Test
		void findByUserId() {
			Member member = new Member("test03", "3333", "다다다", "M", "20001203", 
					"010-3333-3333", "test03@naver.com", "부산시");	
			Member savedMember = repository.save(member);
			
			Member findByUserIdMember = repository.findByUserId(savedMember.getUserId()).get();
			
			assertThat(findByUserIdMember.getUserId()).isEqualTo(savedMember.getUserId());
		}
		
		@Test
		void findByUserName() {
			Member member = new Member("test04", "4444", "라라라", "M", "20001204", 
					"010-4444-4444", "test04@naver.com", "대전시");	
			Member savedMember = repository.save(member);
			
			Member findByUserNameMember = repository.findByUserName(savedMember.getUserName()).get();
			
			assertThat(findByUserNameMember.getUserName()).isEqualTo(savedMember.getUserName());
		}
		
		@Test
		void findAll() {
			List<Member> before = repository.findAll();
			Member member = new Member("test05", "5555", "마마마", "M", "20001205", 
					"010-5555-5555", "test05@naver.com", "대구시");	
			repository.save(member);
			
			List<Member> after = repository.findAll();
			
			assertThat(after.size()).isEqualTo(before.size()+1);
		}
		
		@Test
		void update() {
			Member member = new Member("test06", "6666", "바바바", "M", "20001206", 
					"010-6666-6666", "test06@naver.com", "춘천시");	
			Member savedMember = repository.save(member);
			
			log.info("member : id = " + member.getId());
			log.info("savedMember : id = " + savedMember.getId());
			log.info("savedMember : UserName = " + savedMember.getUserName());
			
			Member updateMember = new Member("test06", "66666", "바바바바", "M", "20011206", 
					"010-6666-0000", "test06B@naver.com", "원주시");	
			repository.update(savedMember.getId(), updateMember);
			
			log.info("updateMember : UserName = " + updateMember.getUserName());
			log.info("savedMember : id = " + repository.findById(savedMember.getId()).get().getId());
			log.info("savedMember : UserName = " + repository.findById(savedMember.getId()).get().getUserName());
			
			assertThat(repository.findById(savedMember.getId()).get().getUserName())
				.isEqualTo(updateMember.getUserName());
		}
		
		@Test
		void authority() {
			Member member = new Member("test07", "7777", "사사사", "M", "20001207", 
					"010-7777-7777", "test07@naver.com", "파주시");	
			Member savedMember = repository.save(member);
			
			repository.authority(savedMember.getId(), Grade.Manager);
			
			assertThat(repository.findById(savedMember.getId()).get().getGrade()).isEqualTo(Grade.Manager);
			}
		
		}
      ~~~
	  ---
	  ![MemberJpaRepository Test](/assets/img/trouble/jparepositorytest.png)

	  ---
	  MemberService

	  ---
	  ~~~java
	@Transactional
	@Service
	public class MemberService {

		private final MemberRepository memberRepository;
			
		public MemberService(MemberRepository memberRepository) {
			this.memberRepository = memberRepository;
		}
				
		// 회원 가입
		public Member join(Member member) {
			return member;
		}
			
		// 회원 정보 조회 - id
		public Optional<Member> findByIdMember(Long id) {
			return memberRepository.findById(id);
		}
			
		// 회원 정보 조회 - userId
		public Optional<Member> findByUserIdMember(String userId) {
			return memberRepository.findByUserId(userId);
		}
		
		// 회원 정보 조회 - userName
		public Optional<Member> findByUserNameMember(String userName) {
			return memberRepository.findByUserName(userName);
		}
		
		// 회원 전체 조회
		public List<Member> findAllMembers() {
			return memberRepository.findAll();
		}
		
		// 회원 정보 수정
		public void updateMember(Long id, Member member) {
			memberRepository.update(id, member);
		}
		
		// 회원 등급 수정
		public void authorityMember(Long id, Grade grade) {
			memberRepository.authority(id, grade);
		}
	}	
	  ~~~
