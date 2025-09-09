# README

본 프로젝트는 **MISO 워크플로우**와 **v0**를 기반으로 구현되었습니다.  
워크플로우는 민원 접수부터 담당자 배정, 중요도 분류 및 확인까지 전 과정을 자동화하도록 설계되었습니다.

### v0 주소 
https://v0-saja-boyz-front-end.vercel.app/

---

## 📌 워크플로우 구성

### 1. GSearch
- **기능**: 민원사항 접수 → AI가 업무 분장 목록과 비교하여 적절한 담당자 판단 → 해당 담당자에게 민원 알림 이메일 전송.
- 접수된 민원은 **문의사항 목록 DB**에 자동 추가됨.

---

### 2. GSearch_list
- **기능**: 로그인한 계정에 배정된 민원사항만을 조회.
- AI가 사전 학습된 중요도 기준에 따라 각 민원의 **중요도를 평가 및 정렬**하여 표시.

---

### 3. GSearch_login
- **기능**: 로그인 관리 플로우.
- 아이디 확인 → 비밀번호 대조 → 로그인 처리.

---

## 🗄️ 데이터베이스 구성

본 프로젝트는 **Google Spreadsheet**를 DB로 연동하여 사용합니다.  
(MISO에서 자체 지원하는 유일한 DB)  

👉 향후 사내 DB로 교체 시, 유연한 연동 및 업데이트 가능.

### 📑 시트 목록

- **문의사항 목록**  
  [문의사항 DB](https://docs.google.com/spreadsheets/d/1MEph2HJT-ExDf82dJiIlM0uL2FAKmJtmI1haqZJuDVQ/edit?usp=sharing)  
  민원 접수 시 자동으로 추가되는 데이터베이스.

- **계정 목록**  
  [계정 DB](https://docs.google.com/spreadsheets/d/1fFKaIvFYxXMmeVeYCB6Mr-u7wWvaZoQz-PzbxIZzvo8/edit?usp=sharing)  
  로그인 가능한 계정 정보.  
  → 추후 인사 DB 또는 **EntraID** 연동 시 대체 가능.

- **담당자 목록**  
  [담당자 DB](https://docs.google.com/spreadsheets/d/1fFKaIvFYxXMmeVeYCB6Mr-u7wWvaZoQz-PzbxIZzvo8/edit?usp=sharing)  
  담당자 입사, 퇴사, 부서 이동 시 업데이트 필요.

- **업무 목록**  
  [업무 DB](https://docs.google.com/spreadsheets/d/1PO5rbFQE-A9wFhSI16CgdL0p9s_8QzUJo69s_yFaekI/edit?usp=sharing)  
  - 첫 번째 열은 **업무 ID** (Primary Key).  
  - 새로운 업무 추가 시 업데이트 필요.

- **업무 배정 목록**  
  [업무 배정 DB](https://docs.google.com/spreadsheets/d/1sA6xlVhXdDIWKqjtEjdA3Dt4UcvVIT6BaD0RCU7z3hw/edit?usp=sharing)  
  - 각 업무 ID에 담당자를 배정한 목록.  
  - 업무 담당자 변경 시 업데이트 필요.

---

## 🔐 로그인

- **조건**: 계정 목록에 등록된 계정만 로그인 가능.  
- **비밀번호 정책**: 현재 모든 계정의 비밀번호는 `1234`로 설정됨.  
  (향후 보안 강화 필요)

---

## 📝 주요 기능 UI

### 1. 민원 입력 창
- 민원 입력 후 **입력 버튼 클릭 시**:
  - 담당자에게 알림 이메일 전송
  - 민원 DB에 자동 추가

### 2. 민원 확인 창
- 로그인된 계정에 배정된 민원 목록 표시
- AI가 학습된 기준에 따라 **중요도 부여 및 정렬**

---

## 🚀 향후 확장 가능성
- Google Spreadsheet DB → **사내 DB** 교체 시, 보다 유연한 연동 가능 및 자동 업데이트 처리 가능. 즉, 화면상에서 민원 응대 및 결과 적용 가능능
- 계정 목록 → **인사 DB / EntraID**와 통합하여 계정 관리 자동화.
