# java-lotto-precourse
로또 발매기 프로젝트

이 프로젝트는 로또 번호를 구매하고, 당첨 번호와 비교해 당첨 내역을 반환하고, 수익률을 계산하는 프로그램입니다.

---

## 기능 목록

### 0. 전체 흐름
- 구입금액 입력
- 발행한 로또수량 출력
- 발행한 로또번호 출력
- 당첨번호 입력
- 보너스 번호 입력
- 당첨 통계 출력
- 총 수익률 출력

#### 실행 결과 예시
```
구입금액을 입력해 주세요.
5000

8개를 구매했습니다.
[8, 21, 23, 41, 42, 43] 
[3, 5, 11, 16, 32, 38] 
[7, 11, 16, 35, 36, 44] 
[1, 8, 11, 31, 41, 42] 
[1, 3, 5, 14, 22, 45]

당첨 번호를 입력해 주세요.
1,2,3,4,5,6

보너스 번호를 입력해 주세요.
7

당첨 통계
---
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
총 수익률은 62.5%입니다.
```

---

### 1. 입력

#### 로또 구입 금액
- 메시지: "구입금액을 입력해 주세요."

#### 당첨 번호 6개 입력
- 로또 번호의 범위는 1~45 사이의 숫자여야 합니다.
- 메시지: "당첨 번호를 입력해 주세요."
- 번호는 쉼표로 구분합니다.
    - 예) `7, 11, 23, 35, 42, 44`
- 입력된 번호가 쉼표로 구분되지 않거나 형식에 맞지 않는 경우 예외처리합니다.

#### 보너스 번호 입력
- 메시지: "보너스 번호를 입력해 주세요."

---

### 2. 예외처리
- 범위 오류: 로또 번호는 반드시 1부터 45 사이의 숫자여야 합니다.
- 형식 오류: 입력이 쉼표로 구분되지 않거나 로또 번호의 형식에 맞지 않는 경우.
- 에러 메시지 형식: `IllegalArgumentException` 발생 시 `[ERROR]`로 시작하는 에러 메시지를 출력하고 해당 부분부터 다시 입력 받습니다.
    - 예) `[ERROR] 로또 번호는 1부터 45 사이의 숫자여야 합니다.`

---

### 3. 처리

#### 로또 발행
- 구입 금액에 따라 로또를 발행합니다.
    - 로또 1장의 가격은 1,000원입니다.
    - 구입 금액이 나누어떨어지지 않는 경우 예외 처리합니다.
- 로또 발행 결과
    - 구입 금액만큼 발행된 로또 번호 목록을 반환합니다.
    - 번호는 오름차순으로 정렬하여 출력합니다.

#### 당첨 확인 및 수익률 계산
- 발행한 로또 번호와 당첨 번호, 보너스 번호를 비교하여 당첨 통계를 반환합니다.
- 당첨 통계에 따라 총 수익률을 계산하고 반환합니다.

---

### 4. 출력

#### 발행한 로또 수량
- 메시지: "x개를 구매했습니다."

#### 발행한 로또 번호 목록
```
[7, 11, 16, 35, 36, 44]
[1, 3, 5, 14, 22, 45]
```
  
#### 당첨 내역
```
당첨 통계
---
3개 일치 (5,000원) - x개
4개 일치 (50,000원) - x개
5개 일치 (1,500,000원) - x개
5개 일치, 보너스 볼 일치 (30,000,000원) - x개
6개 일치 (2,000,000,000원) - x개
```
  
#### 수익률
- 메시지: "총 수익률은 62.5%입니다."
