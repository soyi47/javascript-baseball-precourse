<p align="middle" >
  <img width="200px;" src="https://github.com/woowacourse/javascript-baseball-precourse/blob/main/images/baseball_icon.png?raw=true"/>
</p>
<h1 align="middle">숫자 야구 게임</h1>

<br>

## 🎯 기능 요구사항

### 1. 주어진 요구사항

기본적으로 1부터 9까지 서로 다른 수로 이루어진 3자리의 수를 맞추는 게임이다.

- 같은 수가 같은 자리에 있으면 `스트라이크`, 다른 자리에 있으면 `볼`, 같은 수가 전혀 없으면 `낫싱`이란 힌트를 얻고, 그 힌트를 이용해서 먼저 상대방(컴퓨터)의 수를 맞추면 승리한다.
  - 예) 상대방(컴퓨터)의 수가 425일 때
    - 123을 제시한 경우 : 1스트라이크
    - 456을 제시한 경우 : 1볼 1스트라이크
    - 789를 제시한 경우 : 낫싱
- 위 숫자 야구게임에서 상대방의 역할을 컴퓨터가 한다. 컴퓨터는 1에서 9까지 서로 다른 임의의 수 3개를 선택한다. 게임 플레이어는 컴퓨터가 생각하고 있는 3개의 숫자를 입력하고, 컴퓨터는 입력한 숫자에 대한 결과를 출력한다.
- 이 같은 과정을 반복해 컴퓨터가 선택한 3개의 숫자를 모두 맞히면 게임이 종료되고, 재시작 버튼이 노출된다.
- 게임이 종료된 후 재시작 버튼을 클릭해 게임을 다시 시작할 수 있다.
- 사용자가 잘못된 값을 입력한 경우 `alert`으로 에러 메시지를 보여주고, 다시 입력할 수 있게 한다.

#### 게임의 흐름

1. 컴퓨터 랜덤 값 생성하기 (서로 다른 3자리의 랜덤 숫자)

2. 사용자 입력 값 받기

   - 잘못된 값 입력 시 `alert`로 에러 메시지 띄우고 다시 입력 받음

     잘못된 값의 경우는 다음과 같다.

     - 3자리가 아닌 경우

     - 각 자리가 1~9가 아닌 경우 (0이 포함된 경우)
     - 각 자리 숫자가 중복되는 경우

3. 컴퓨터의 랜덤 값과 사용자 입력 값 비교하기

   - 같은 수가 같은 자리에 있으면 스트라이크 += 1

   - 같은 수가 다른 자리에 있으면 볼 += 1

4. 결과 출력하기

   - 정답인 경우, 게임 종료

     - 스트라이크가 3이면 정답

     - 정답 문구와 게임 재시작 버튼 출력하며 게임 종료

       게임을 재시작 하는 경우 '1. 컴퓨터 랜덤 값 생성하기'부터 다시 시작.

   - 정답이 아닌 경우, 힌트 출력

     - 스트라이크가 3이 아니면 오답
     - 스트라이크와 볼의 수가 둘다 0이면 힌트 "낫싱" 출력
     - 위 조건에 해당 안 되면, 볼과 스트라이크 수를 힌트로 출력
     - '2. 사용자 입력 값 받기'로 이동

<br>

### 2. 구현할 기능 목록

- [x] 게임을 초기화하는 기능 | `initGame`
  - 컴퓨터가 가지는 3자리 숫자를 새로 지정하고
  - 결과 문구, 사용자 입력창의 value를 clear하고
  - 재시작 안내 문구를 숨김
- [x] 컴퓨터가 가지는 서로 다른 3자리의 랜덤 숫자 생성하는 기능 | `createComputerNumbers`
- [x] 사용자 입력창을 clear하는 기능 | `clear - UserInput`
- [x] 결과 문구를 clear하는 기능 | `clearResult - Guide`
- [x] 재시작 안내 문구를 숨기는 기능 | `hideRestart - Guide`
- [x] 사용자가 입력한 숫자의 정답 비교 결과를 사용자가 확인할 수 있도록 하는 기능 | `checkAnswer`
  - 사용자 입력 값을 가져와 잘못된 값인지 확인하고,
  - 잘못된 경우
    - `alert`로 에러 메시지 띄우고
    - 결과 문구와 사용자 입력창 clear
  - 잘못되지 않은 경우
    - 컴퓨터 숫자와 사용자 입력 숫자 비교하여 결과 문구 띄우기
    - 정답인 경우 재시작 안내 문구 띄우기
- [x] 사용자의 현재 입력 값을 가져오는 기능 | `getNumbers - UserInput `
- [x] 사용자의 입력 값이 잘못된 값인지 확인하여 true/false로 return | `isValid - UserInput`
  - [x] 입력이 세 자리 숫자인지 확인 | `isThreeDigit - UserInput`
  - [x] 입력이 각 자리 숫자가 제시된 숫자 범위 1~9에 속하는지 확인 | `isRangeCorrect - UserInput`
  - [x] 입력이 각 자리 숫자가 중복되지 않는지 확인 | `isNotDuplicated - UserInput`
- [x] 두 숫자를 비교하여 볼과 스트라이크의 수를 카운트하는 기능 | `play`
  - 볼과 스트라이크의 수를 세고
  - 문자열 형태로 결과를 return함
  - [x] 두 숫자를 비교하여 볼의 수를 카운트하는 기능 | `getNumberOfBalls`
  - [x] 두 숫자를 비교하여 스트라이크의 수를 카운트하는 기능 | `getNumberOfStrikes`
- [x] 결과 문구를 띄우는 기능 | `printResult - Guide`
- [x] 재시작 안내 문구를 띄우는 기능 | `showRestart - Guide`
  - 재시작 버튼을 누르면 게임을 다시 시작할 수 있도록 함.

