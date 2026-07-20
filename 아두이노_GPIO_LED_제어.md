## GPIO를 사용하여 LED 제어

Thinkcad에서 아두이노를 시뮬레이션하여 구현하였다.

 코드
void setup() {
  pinMode(8, OUTPUT);
}

void loop() {
  digitalWrite(8, HIGH);
  delay(1000);
  digitalWrite(8, LOW);
  delay(1000);
}

## 모스 부호로 S.O.S 신호 생성

모스 부호는 글자와 숫자를 짧은 신호와 긴 신호의 조합으로 나타내는 통신 방식이다.
아두이노에 LED를 연결하여 점멸 주기를 조정하므로써 모스 부호를 표현할 수 있다.

코드 : S.O.S 신호 반복

const int LED_PIN = 8;
const int unit = 200;  // 기본 시간: 0.2초

void dot() {
  digitalWrite(LED_PIN, HIGH);
  delay(unit);
  digitalWrite(LED_PIN, LOW);
  delay(unit);
}

void dash() {
  digitalWrite(LED_PIN, HIGH);
  delay(unit * 3);
  digitalWrite(LED_PIN, LOW);
  delay(unit);
}

void setup() {
  pinMode(LED_PIN, OUTPUT);
}

void loop() {
  // S: · · ·
  dot();
  dot();
  dot();

  delay(unit * 2);  // 글자 사이 간격

  // O: — — —
  dash();
  dash();
  dash();

  delay(unit * 2);

  // S: · · ·
  dot();
  dot();
  dot();

  delay(unit * 7);  // SOS를 다시 보내기 전 간격
}

## 프로그램 작동 원리

아두이노의 GPIO 8번 핀에 연결된 LED를 HIGH일때 키고 LOW일때 끄도록 하여 S.O.S 모스 부호를 표현한다.
여기서 점(.)은 짧은 점등, 선(-)은 긴 점등으로 표현한다.

 pinMode(8, OUTPUT) // 8번 핀을 출력용으로 설정
 digitalWrite(8, HIGH or LOw) // LED 온오프
 delay() // LED 점등 주기 조절 Ex. delay(200)이면 0.2초 지연

## 아두이노 GPIO 핀 제어

GPIO는 아두이노가 전기 신호를 입출력하는 핀이다. LED 제어에는 출력모드인 OUTPUT을 사용하고, LED에는 과전류 방지를 위해 저항을 직렬로 연결한다.

## 외부 전원어댑터를 활용하여 LED 여러 개 사용
LED를 여러 개 사용하는 경우에는 GPIO를 통해 직접 전원을 공급하는 것이 아닌, 외부 어댑터를 사용한다. GPIO는 MOSFET이나 트랜지스터를 제어하는 용도로 사용하며, 아두이노 GND와 외부 전원 GND는 연결해야 한다.

필요한 전류는 다음과 같이 계산할 수 있다.
 LED 1개 전류 × LED 개수 = 총 필요 전류

위 계산식을 활용하면 적절한 어댑터를 선택할 수 있다. 예를 들어 LED 10개가 각각 20mA라면 20mA * 10 = 200mA = 0.2A 이다. 따라서 여유롭게 사용하기 위해 5V 1A 어댑터를 선택하면 된다.