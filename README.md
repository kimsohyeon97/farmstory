## 개요
- 프로젝트 이름 : FarmStory
- 프로젝트 지속기간 : 2025.02.10-2025.03.07
- 개발 엔진 및 언어: Eclipse & Mysql & JAVA & JavsScript  
- 팀 : 4조 
<br><br>
## 사용 기술
![js](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![js](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=JavaScript&logoColor=white)
![js](https://img.shields.io/badge/CSS-239120?&style=for-the-badge&logo=css3&logoColor=white)
![js](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![js](https://img.shields.io/badge/MySQL-00000F?style=for-the-badge&logo=mysql&logoColor=white) <br><br>

## 내가 구현한 기능 
자세한 코드 리뷰 : https://fish-fahrenheit-662.notion.site/1-2044ffb4f47b80b5a0aac27e4cf8e483?source=copy_link
### 1️⃣ 약관 동의 페이지 (Terms Agreement)

> JSP + Servlet 기반의 약관 및 개인정보 처리방침 동의 기능을 구현하였습니다.

- **JSP/Servlet 기반 MVC 구조 설계**
- **약관 데이터 조회 (DB → DAO → DTO → JSP 바인딩)**
- **Vanilla JS 유효성 검사**로 동의 체크 여부 확인
- **Singleton 패턴 서비스 계층**, 계층 간 명확한 역할 분리
- View는 `/WEB-INF` 하위에 배치하여 직접 접근 방지

사용 기술: Java, JSP, Servlet, DAO 패턴, DTO, MVC, JavaScript


### 2️⃣ 회원가입 기능 (Register)

> 사용자로부터 개인정보를 입력받아 DB에 등록하는 회원가입 기능을 구현하였습니다.  
> 아이디, 별명, 이메일, 휴대폰은 서버 중복 체크 및 정규식 유효성 검사를 수행하며, 이메일은 인증코드 검증을 통해 보안성을 강화하였습니다.

- **JSP + Servlet 기반 MVC 구조 구현**
- **비밀번호 SHA-256 해시 처리로 보안 강화**
- **JavaScript 정규식 유효성 검사 + Fetch 기반 중복 체크**
- **Daum 주소 API 연동**으로 우편번호 자동 입력
- **이메일 인증 로직 구현** (코드 생성 → 이메일 발송 → 세션 저장 → 인증 비교)

사용 기술: Java, JSP, Servlet, SHA-256, JavaScript, Daum Postcode API, Gmail SMTP, Fetch API

### 3️⃣ 로그인 기능 (Login)

> 아이디와 비밀번호를 입력받아 DB에서 검증 후, 세션에 사용자 정보를 저장하여 로그인 상태를 유지합니다.

- **SHA-256 해시 기반 비밀번호 인증**
- **JSP + Servlet 기반 MVC 구조로 구현**
- **로그인 성공 시 세션(`sessUser`)에 사용자 정보 저장**
- **실패/로그아웃 상태는 JS alert로 안내**
- **비밀번호는 SQL에서 직접 SHA2 해시로 비교하여 DB 조회**

사용 기술: Java, JSP, Servlet, DAO 패턴, SHA-256, Session, JavaScript

### 4️⃣ 로그아웃 기능 (Logout)

> 로그인된 사용자의 세션을 초기화하고, 로그인 페이지로 리다이렉트하여 로그아웃을 처리합니다.

- **GET 방식 로그아웃 요청 처리**
- **세션 속성 제거 및 invalidate() 호출로 보안 로그아웃 수행**
- **로그인 페이지 리다이렉트 후 JS alert 메시지로 알림 처리**
- **result=101 쿼리 파라미터를 통해 로그아웃 메시지 분기 처리**

사용 기술: Java, JSP, Servlet, Session

### 5️⃣ 아이디 찾기 기능 (Find User ID with Email Verification)

> 이름과 이메일을 입력하면 인증번호를 이메일로 발송하고, 사용자가 이를 입력해 인증에 성공하면 아이디를 확인할 수 있는 기능입니다.

- **이름 + 이메일 기반 사용자 조회 및 검증**
- **SMTP를 활용한 인증번호 이메일 발송**
- **세션 기반 인증번호 저장 처리**
- **인증 성공 여부에 따라 다음 단계 이동 가능**
- **Fetch 기반 AJAX 요청으로 UX 개선**

사용 기술: Java, JSP, Servlet, Session, JSON, Fetch API, Gmail SMTP

### 6️⃣ 아이디 찾기 결과 화면 (Find User ID Result)

> 이메일 인증을 완료한 사용자에게 아이디 및 관련 정보를 결과 페이지에서 출력합니다.

- **세션에서 사용자 정보(`sessUser`)를 안전하게 추출**
- **이름, 아이디, 이메일, 가입일 등을 표 형식으로 표시**
- **직접 파라미터 전달 없이 서버 내 보안 처리**
- **JSP는 /WEB-INF 경로 내에 배치하여 직접 접근 차단**

사용 기술: Java, JSP, Servlet, Session

### 7️⃣ 비밀번호 찾기 기능 (Password Recovery via Email Verification)

> 아이디와 이메일을 입력하면, 인증번호가 이메일로 발송되고, 인증에 성공한 경우 비밀번호 변경 페이지로 이동합니다.

- **아이디 + 이메일 조합으로 사용자 존재 여부 검증**
- **SMTP 기반 이메일 인증번호 발송 (JavaMail API)**
- **인증번호를 서버 세션에 저장하여 인증 상태 관리**
- **비동기 Fetch API를 통해 UX 개선**
- **클라이언트 측 인증번호 비교 및 인증 성공 시 다음 단계 활성화**

사용 기술: Java, JSP, Servlet, Session, JSON, Fetch API, Gmail SMTP

### 8️⃣ 비밀번호 변경 기능 (Change Password)

> 인증된 사용자가 새 비밀번호를 입력하여 계정을 갱신할 수 있는 기능입니다.

- **비밀번호 변경 전 세션 기반 사용자 인증 확인**
- **JavaScript로 비밀번호 일치 여부 사전 확인**
- **비밀번호 변경 완료 후 세션 무효화 및 로그인 페이지로 리다이렉트**
- **비밀번호는 SQL로 직접 업데이트 (⚠ 현재 해시 미적용 → 개선 필요)**

사용 기술: Java, JSP, Servlet, Session, JDBC


