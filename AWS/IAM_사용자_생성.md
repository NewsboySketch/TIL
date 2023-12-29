# AWS IAM 개요 및 사용자 생성 실습

## 개요
AWS 클라우드 시스템 공동 사용을 위한 IAM 계정 생성 절차


## IAM 이란?

* Identity and Access Management의 약자로, AWS 계정 및 권한 관리 서비스

* AWS 서비스와 리소스에 대한 엑세스 관리

* 사용자, 그룹, 역할, 정책으로 구성

* 리전이 아닌 글로벌 서비스


### 계정 보안 강화를 위한 권장 사항

* Root 계정(본인 AWS 계정)은 생성 이후 가능하면 사용 X
* 최소 권한만 부여된 사용자 계정(IAM 계정)으로 서비스 사용
* Root 계정과 개별 사용자 계정에 MFA(멀티팩터 인증) 적용
* 암호 복잡성 요구 사항 및 의무 교체 주기 정의(60~90일)

### 사용자, 그룹, 역할, 정책

사용자(User) - 개인 or 애플리케이션을 위한 **특정 권한을 가진 ID**

* 한 명의 실제 사용자와 연관
* 암호(사용자의 콘솔 로그인) or 엑세스 키(애플리케이션의 접속)로 엑세스 가능


그룹(Group) - 개발팀, 운영팀 등의 **사용자 집합**

역할(Role) - 특정 개인에 속하지 않는 **특정 권한을 가진 ID**

정책(Policy) - 사용자, 그룹, 역할에 연결하여 사용, JSON 문서 형식

## 사용자 생성 실습 절차

1. Root 계정 IAM 활성화
2. 관리용 IAM 사용자 생성
3. 개발용 IAM 사용자 생성

### 1. Root 계정 IAM 활성화

1. 기본적으로 생성한 자신의 계정 (=Root 계정)으로 로그인
2. 우측 상단 계정 이름 > **계정** 클릭
   
   <img width="400" alt="스크린샷 2023-12-28 오후 11 04 58" src="https://github.com/NewsboySketch/TIL/assets/42952156/ed2e8a1b-5919-40a3-98ab-3bbf653c1d6d">


3. 결제 정보에 대한 IAM 사용자 및 역할 액세스 활성화 > 업데이트
   <img width="1356" alt="스크린샷 2023-12-28 오후 11 05 46" src="https://github.com/NewsboySketch/TIL/assets/42952156/78d33f6e-7b67-45d8-bd5d-e382f9485671">


### 2. 관리용 IAM 사용자 생성

1. IAM 검색 및 이동 > 사용자(Users) 클릭
2. 사용자명 지정 (administrator, admin 등)
3. AWS 콘솔 엑세스 권한 제공 체크, IAM 사용자 직접 생성 체크
   
    * ID 센터 : 계정 관리 서비스
   <img width="1728" alt="스크린샷 2023-12-28 오후 11 08 31" src="https://github.com/NewsboySketch/TIL/assets/42952156/2e1d5bb3-89f6-4bb6-a3ae-d885b07f7af1">
4. 그룹에 사용자 추가 > 그룹 생성 (Admin 등), AdministratorAccess 정책 체크 > 사용자 그룹 생성 > 해당 그룹 체크 후 사용자 생성
   <img width="1723" alt="스크린샷 2023-12-28 오후 11 09 07" src="https://github.com/NewsboySketch/TIL/assets/42952156/3c27ad6b-2004-4bb1-a2c6-3f044ce30315">
   <img width="1398" alt="스크린샷 2023-12-28 오후 11 10 20" src="https://github.com/NewsboySketch/TIL/assets/42952156/3aabc4c7-7e88-4447-b5ce-842a93dab487">


5. 콘솔 로그인 링크를 접속해 로그인
   <img width="981" alt="image" src="https://github.com/NewsboySketch/TIL/assets/42952156/ff181808-e3e4-4135-84ed-e4902dff87b7">


### 3. 개발용 IAM 사용자 생성

1. 위 2와 같은 절차이나, PowerUserAccess 정책으로 새 그룹을 생성하여 사용자에 적용
   <img width="828" alt="스크린샷 2023-12-28 오후 11 22 15" src="https://github.com/NewsboySketch/TIL/assets/42952156/922a75bc-2b90-4755-b413-c71f45860a6e">

   <img width="1339" alt="스크린샷 2023-12-28 오후 11 23 25" src="https://github.com/NewsboySketch/TIL/assets/42952156/7a15a47c-1796-4f32-b8a7-4657d57c4224">


