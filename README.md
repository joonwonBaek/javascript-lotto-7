# 로또 미션 💰

## 구현 기능 목록

### 입력

#### 구매할 로또 금액 입력 받기

- 사용자는 로또 구매 금액을 입력한다.
- 입력 받은 금액이 1,000원 단위인지 확인한다.
- 1,000원 단위로 나누어 떨어지지 않을 경우, "[ERROR] 1000원 단위로 입력해야 합니다." 메시지를 출력하고 재입력 받는다.

#### 당첨 번호 및 보너스 번호 입력 받기

- 사용자는 쉼표로 구분된 6개의 당첨 번호를 입력한다.
- 추가로 보너스 번호 1개를 입력한다.
- 입력된 당첨 번호와 보너스 번호가 중복되지 않고 1~45 사이의 숫자인지 확인한다.
- 유효하지 않은 번호가 입력될 경우, "[ERROR] 로또 번호는 1부터 45 사이의 숫자여야 합니다." 메시지를 출력하고 재입력 받는다.

### 로또 생성

- 사용자가 입력한 금액을 기준으로 로또 1장당 1,000원으로 구매할 수 있는 로또 개수를 계산한다.
- 계산된 로또 개수만큼 중복되지 않는 1~45 사이의 랜덤한 숫자 6개로 구성된 로또를 생성한다.
- 생성된 로또 번호는 오름차순으로 정렬된다.

### 로또 당첨 번호 추첨

- 당첨 번호: 중복되지 않는 6개의 번호를 뽑는다.

- 보너스 번호: 추가로 중복되지 않는 보너스 번호 1개를 뽑는다.

### 로또 당첨 확인

- 당첨 번호와 구매한 로또 번호 비교

- 구매한 각 로또 번호와 당첨 번호를 비교한다. 일치하는 번호의 개수를 세고, 보너스 번호와도 일치 여부를 확인한다.
- 당첨 등수 계산: 각 로또가 몇 개의 번호를 일치시켰는지, 보너스 번호를 포함하는지 확인하여 등수를 판별한다.
- 등수별 당첨 기준
  - 1등: 6개 번호 일치 (2,000,000,000원)
  - 2등: 5개 번호 + 보너스 번호 일치 (30,000,000원)
  - 3등: 5개 번호 일치 (1,500,000원)
  - 4등: 4개 번호 일치 (50,000원)
  - 5등: 3개 번호 일치 (5,000원)
  - 각 등수의 당첨 로또 수를 세고, 당첨 내역을 출력한다.

### 수익률 계산

- 총 당첨금과 구매 금액을 기준으로 수익률을 계산하고, 소수점 둘째 자리에서 반올림하여 출력한다.

### 예외 처리

- 구입 금액 오류 처리: 구입 금액이 1,000원 단위가 아닌 경우 "[ERROR] 구입 금액은 1,000원 단위로 입력해야 합니다." 메시지 출력 후 다시 입력 받는다.
- 로또 번호 범위 오류: 입력한 번호가 1부터 45 사이의 숫자가 아닌 경우 "[ERROR] 로또 번호는 1부터 45 사이의 숫자여야 합니다." 메시지 출력 후 다시 입력 받는다.
- 보너스 번호 범위 오류: 보너스 번호가 1부터 45 사이의 숫자가 아닌 경우 "[ERROR] 보너스 번호는 1부터 45 사이의 숫자여야 합니다." 메시지 출력 후 다시 입력 받는다.

### 출력

#### 구매한 로또 갯수 및 번호 출력

- 사용자가 입력한 금액을 기준으로 구매할 수 있는 로또 개수를 계산하여 출력한다.
- 각 로또 번호는 중복되지 않게 1~45 사이의 랜덤 번호 6개로 구성되며, 오름차순으로 정렬되어 출력된다.

#### 당첨 번호 및 보너스 번호 출력

- 사용자가 입력한 6개의 당첨 번호와 보너스 번호를 출력한다.

## 테스트 항목

### Lotto 클래스 테스트

- 로또 번호의 개수 검사: 로또 번호가 6개보다 많거나 적을 경우, 예외가 발생하는지 테스트
- 중복 번호 검사: 로또 번호에 중복된 숫자가 있으면 예외를 발생시키는지 확인
- 범위 검사: 로또 번호가 1보다 작거나 45보다 큰 경우 예외가 발생하는지 테스트
- 정상 생성 테스트: 중복 없고 유효한 범위의 로또 번호로 로또가 정상적으로 생성되는지 테스트

### LottoController 클래스 테스트

- 구매 금액 검사: 구매 금액이 1,000원 단위가 아닌 경우, 최소 금액보다 적은 경우, 숫자가 아닌 값이 입력된 경우 예외를 발생시키는지 테스트
- 당첨 번호 검사: 당첨 번호가 6개가 아니거나 중복된 숫자, 범위를 벗어난 숫자가 포함된 경우 예외를 발생시키는지 테스트
- 보너스 번호 검사: 보너스 번호가 당첨 번호와 중복되거나 유효 범위를 벗어나는 경우 예외를 발생시키는지 확인
- 로또 개수 계산: 구매 금액에 따라 몇 장의 로또를 구매할 수 있는지 정확하게 계산하는지 테스트
- 당첨 결과 계산: 당첨 번호와 보너스 번호를 기준으로 각 등수별 당첨 결과를 올바르게 계산하는지 확인
