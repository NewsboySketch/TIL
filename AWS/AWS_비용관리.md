# AWS 비용관리

## 개요
* AWS Budgets, AWS Cost Explorer, AWS Cost and Usage Report 탐색
* 프리 티어 정책 위반 시 리소스 해제 Budget 생성 실습
* 고정 예산 초과 시 알림 및 리소스 해제 Budget 생성 실습

#### AWS Budgets

* 예산을 지정하여 비용과 사용량을 추적하는 서비스 
* 비용이나 사용량이 사전에 설정한 임계값을 초과할 때, 알림을 받거나 중지하는 작업을 연결 가능 
* 리전, 계정, 태그별 상세 예산 설정이 가능

#### AWS Cost Explorer

* AWS 비용 및 사용량을 시각적으로 분석 가능
* 서비스별, 계정별 + 시간별, 일별, 월별 사용량 및 비용 확인 및 보고서 생성
* 지난 데이터를 통해 예상 지출 금액 예측 가능

#### AWS Cost and Usage Report

* AWS 비용 및 사용에 대한 가장 상세한 보고서 제공
* 활성화한 월부터 데이터 수집
* 생성된 보고서 파일을 S3 버킷으로 전송 가능


### AWS Budgets 실습

#### 프리 티어 정책 위반 시 알림 Budget 생성 실습

1. AWS Budgets 이동 및 예산 생성 클릭
  <img width="1000" alt="스크린샷 2024-01-03 오후 9 45 44" src="https://github.com/NewsboySketch/TIL/assets/42952156/19713b68-a057-4c2f-af58-c695cfa43dfc">

2. 템플릿에서 제로 지출 예산 선택 후 트리거 시 수신할 이메일 입력
  <img width="500" alt="스크린샷 2024-01-03 오후 10 00 14" src="https://github.com/NewsboySketch/TIL/assets/42952156/6bb84f76-5d80-4d22-98ad-498a889b865b">

3. 완료
  <img width="500" alt="스크린샷 2024-01-03 오후 10 00 58" src="https://github.com/NewsboySketch/TIL/assets/42952156/badf5138-7603-4929-894c-67ac9d8768cb">

  


#### 고정 예산 초과 시 알림 및 리소스 해제 Budget 생성 실습

1. AWS Budgets 이동 및 예산 생성 클릭
  <img width="1000" alt="스크린샷 2024-01-03 오후 9 39 59" src="https://github.com/NewsboySketch/TIL/assets/42952156/383eb180-98db-4f61-bf5a-3fbe3caee902">

2. 사용자 지정, 비용 예산 선택
  <img width="500" alt="스크린샷 2024-01-03 오후 9 40 39" src="https://github.com/NewsboySketch/TIL/assets/42952156/61d4a22b-a249-421a-9293-4cc5f8548d3f">

3. 예산 이름, 기간, 예산 금액 등 입력
  <img width="500" alt="스크린샷 2024-01-03 오후 9 41 58" src="https://github.com/NewsboySketch/TIL/assets/42952156/d30c818a-12b3-482e-9a08-cf3be36159e3">

4. 알림 임계값(%) 입력 후 트리거 시 수신할 이메일 입력
  <img width="400" alt="스크린샷 2024-01-03 오후 9 43 16" src="https://github.com/NewsboySketch/TIL/assets/42952156/57fb4000-2486-42f8-9b95-cb620aac10e6">

5. 필요 시 중지할 인스턴스 및 그에 필요한 IAM 역할(Role) 지정
  <img width="400" alt="스크린샷 2024-01-03 오후 9 45 16" src="https://github.com/NewsboySketch/TIL/assets/42952156/4bc127f8-e87a-440a-a31a-0263eafda539">

6. 완료
  <img width="1000" alt="스크린샷 2024-01-03 오후 9 45 44" src="https://github.com/NewsboySketch/TIL/assets/42952156/bea512c1-1747-4e4c-b0db-8bc324f7f22c">
