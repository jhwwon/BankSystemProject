# 🏦 Bank Account Management System

> Java 기반의 완전한 은행 계좌 관리 시스템

[![Java](https://img.shields.io/badge/Java-11+-orange.svg)](https://www.oracle.com/java/)
[![Oracle](https://img.shields.io/badge/Oracle-Database-red.svg)](https://www.oracle.com/database/)
[![Lombok](https://img.shields.io/badge/Lombok-1.18.30-pink.svg)](https://projectlombok.org/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

## 📋 목차

- [프로젝트 개요](#-프로젝트-개요)
- [주요 기능](#-주요-기능)
- [시스템 구조](#-시스템-구조)
- [기술 스택](#-기술-스택)
- [설치 및 실행](#-설치-및-실행)
- [데이터베이스 설정](#-데이터베이스-설정)
- [사용법](#-사용법)
- [프로젝트 구조](#-프로젝트-구조)
- [API 문서](#-api-문서)
- [기여하기](#-기여하기)
- [라이선스](#-라이선스)

## 🎯 프로젝트 개요

이 프로젝트는 Java를 사용하여 구현된 완전한 은행 계좌 관리 시스템입니다. 실제 은행의 핵심 기능들을 구현하여 사용자와 관리자 모두를 위한 포괄적인 서비스를 제공합니다.

### ✨ 핵심 특징

- 🔐 **안전한 인증 시스템**: 사용자 및 관리자 로그인
- 💰 **다양한 계좌 타입**: 보통예금, 정기예금, 적금
- 🔄 **실시간 거래 처리**: 입금, 출금, 이체
- 📊 **자동 이자 계산**: 매월 자동 이자 지급
- 👨‍💼 **관리자 대시보드**: 전체 시스템 관리
- 📈 **거래 내역 추적**: 상세한 거래 기록

## 🚀 주요 기능

### 👤 사용자 기능
- **회원 관리**
  - 회원가입 및 로그인
  - 개인정보 수정
  - 계정 관리

- **계좌 관리**
  - 계좌 생성 (보통예금, 정기예금, 적금)
  - 계좌 조회 및 관리
  - 계좌 해지
  - 계좌 비밀번호 변경

- **거래 서비스**
  - 입금/출금
  - 계좌 간 이체
  - 거래 내역 조회
  - 실시간 잔액 확인

### 👨‍💼 관리자 기능
- **계좌 관리**
  - 전체 계좌 조회
  - 사용자별 계좌 조회
  - 계좌 상태 관리

- **이자 관리**
  - 수동 이자 지급
  - 이자 지급 내역 조회
  - 이자율 설정

- **시스템 관리**
  - 스케줄러 상태 모니터링
  - 시스템 로그 관리
  - 자동화 작업 관리

### ⚙️ 자동화 기능
- **스케줄러**
  - 매월 마지막 날 자동 이자 지급
  - 백그라운드 작업 처리
  - 시스템 상태 모니터링

## 🏗️ 시스템 구조

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│사용자 인터페이스  │    │   비즈니스 로직 │    │   데이터베이스    │
│   (Terminal UI) │◄──►│   (Managers)    │◄──►│   (Oracle DB)   │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## 🛠️ 기술 스택

### Backend
- **Java 11+** - 메인 프로그래밍 언어
- **Oracle Database** - 데이터 저장소
- **JDBC** - 데이터베이스 연결

### Libraries
- **Lombok** - 코드 간소화 (getter/setter 자동 생성)
- **Oracle JDBC Driver** - Oracle 데이터베이스 연결

### Development Tools
- **Maven/Gradle** - 의존성 관리 (선택사항)
- **IDE** - IntelliJ IDEA, Eclipse, VS Code

## 📦 설치 및 실행

### 1. 사전 요구사항
- Java 11 이상
- Oracle Database 11g 이상
- Oracle JDBC Driver

### 2. 프로젝트 클론
```bash
git clone https://github.com/yourusername/bank-system.git
cd bank-system
```

### 3. 라이브러리 설정
`lib/` 폴더에 다음 JAR 파일들을 배치하세요:
- `lombok-1.18.30.jar`
- `ojdbc8-21.9.0.0.jar`

### 4. 컴파일
```bash
# src 폴더로 이동
cd src

# Java 파일 컴파일
javac -cp "../lib/*" banksystem/*.java banksystem/*/*.java

# 컴파일된 클래스 파일을 bin 폴더로 이동
mkdir -p ../bin
cp -r banksystem ../bin/
```

### 5. 실행
```bash
# 프로젝트 루트에서 실행
java -cp "bin:lib/*" banksystem.BankSystem
```

## 🗄️ 데이터베이스 설정

### 1. Oracle Database 설치
Oracle Database 11g 이상 버전을 설치하세요.

### 2. 데이터베이스 생성
```sql
-- 사용자 생성
CREATE USER jhw1 IDENTIFIED BY 1234;
GRANT CONNECT, RESOURCE TO jhw1;
GRANT CREATE TABLE TO jhw1;
GRANT CREATE SEQUENCE TO jhw1;
```

### 3. 테이블 생성
`sqls/banksystem.sql` 파일을 실행하여 테이블을 생성하세요:
```bash
sqlplus jhw1/1234@localhost:1521/orcl @sqls/banksystem.sql
```

### 4. 연결 정보 수정
`BankSystem.java` 파일에서 데이터베이스 연결 정보를 수정하세요:
```java
conn = DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521/orcl", "jhw1", "1234");
```

## 📖 사용법

### 1. 시스템 시작
```bash
java -cp "bin:lib/*" banksystem.BankSystem
```

### 2. 메인 메뉴
```
-- 은행 계좌 관리 시스템 --
계좌 서비스를 이용하려면 로그인해주세요.
✅ 자동 이자 지급: 다음 실행: 2024-01-31 14:00:00

✅ 메인메뉴: 1.회원가입 | 2.사용자 로그인 | 3.관리자 로그인 | 4.종료
```

### 3. 사용자 로그인 후 메뉴
```
✅ 계좌관리    ✅ 거래업무    ✅ 기타설정    ✅ 시스템
1. 계좌생성    4. 입금       8. 계좌비밀번호변경   10. 로그아웃
2. 계좌조회    5. 출금       9. 회원정보수정     0. 종료
3. 계좌해지    6. 이체
              7. 거래내역조회
```

### 4. 관리자 로그인 후 메뉴
```
✅ 계좌관리        ✅ 이자관리        ✅ 시스템관리        ✅ 기타
1. 전체계좌조회    3. 수동이자지급    5. 스케줄러상태      6. 로그아웃
2. 사용자별계좌조회 4. 이자지급내역조회 0. 종료
```

## 📁 프로젝트 구조

```
BankSystemProject/
├── src/                           # 소스 코드
│   └── banksystem/
│       ├── BankSystem.java        # 메인 클래스
│       ├── entity/                # 엔티티 클래스
│       │   ├── User.java
│       │   ├── Account.java
│       │   ├── Transaction.java
│       │   ├── InterestInfo.java
│       │   └── InterestPayment.java
│       ├── manager/               # 비즈니스 로직
│       │   ├── UserManager.java
│       │   ├── AccountManager.java
│       │   ├── TransactionManager.java
│       │   ├── AdminManager.java
│       │   └── SchedulerManager.java
│       ├── helper/                # 헬퍼 클래스
│       │   ├── InputHelper.java
│       │   └── ValidationHelper.java
│       └── util/                  # 유틸리티
│           ├── BankUtils.java
│           └── InterestCalculator.java
├── bin/                           # 컴파일된 클래스
├── lib/                           # 라이브러리
│   ├── lombok-1.18.30.jar
│   └── ojdbc8-21.9.0.0.jar
├── sqls/                          # 데이터베이스 스크립트
│   └── banksystem.sql
├── README.md                      # 프로젝트 문서
└── LICENSE                        # 라이선스
```

## 📚 API 문서

### 주요 클래스

#### BankSystem
시스템의 메인 클래스로 전체 애플리케이션의 진입점입니다.

#### UserManager
사용자 관련 기능을 담당합니다.
- `join()` - 회원가입
- `login()` - 로그인
- `modifyUserInfo()` - 회원정보 수정

#### AccountManager
계좌 관련 기능을 담당합니다.
- `createAccount()` - 계좌 생성
- `readAccount()` - 계좌 조회
- `deleteAccount()` - 계좌 해지
- `changePassword()` - 계좌 비밀번호 변경

#### TransactionManager
거래 관련 기능을 담당합니다.
- `deposit()` - 입금
- `withdraw()` - 출금
- `transfer()` - 이체
- `history()` - 거래내역 조회

#### AdminManager
관리자 기능을 담당합니다.
- `viewAllAccounts()` - 전체 계좌 조회
- `viewUserAccounts()` - 사용자별 계좌 조회
- `executeInterestPayment()` - 이자 지급
- `viewInterestHistory()` - 이자 지급 내역 조회

## 🤝 기여하기

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### 기여 가이드라인
- 코드 스타일은 Java 표준 컨벤션을 따릅니다
- 새로운 기능 추가 시 테스트 코드를 포함해주세요
- 커밋 메시지는 명확하고 간결하게 작성해주세요

## 📄 라이선스

이 프로젝트는 MIT 라이선스 하에 배포됩니다. 자세한 내용은 [LICENSE](LICENSE) 파일을 참조하세요.

## 📞 연락처

프로젝트 링크: [https://github.com/yourusername/bank-system](https://github.com/yourusername/bank-system)

## 🙏 감사의 말

이 프로젝트는 교육 목적으로 개발되었으며, 실제 은행 시스템의 복잡성을 이해하는 데 도움이 되기를 바랍니다.

---

⭐ 이 프로젝트가 도움이 되었다면 Star를 눌러주세요!
