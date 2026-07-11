## 아두이노 센서 데이터 읽기
아두이노를 사용하여 온도, 조도, 거리 등의 데이터를 센서를 통하여 측정할 수 있다.
각 센서를 아두이노에 연결하는 방법은 다음과 같다.

1. 온도 센서 연결

 온도 센서 : DHT11(or DHT22)
 연결 방법 : DHT11 VCC - Arduino 5V
                  GND - GND
                  DATA - D2(디지털 핀)
 DHT11의 DATA와 VCC 사이에 10kΩ 풀업 저항을 연결하면 안정적으로 동작한다.

2. 조도 센서 연결

 조도 센서 : LDR 모듈
 연결 방법 : 조도 센서(LDR) VCC - Arduino 5V
                         GND - GND
                         A0 - A0

3. 거리 센서 연결

 거리 센서 : HC-SR04 초음파 센서
 연결 방법 : HC-5R04 VCC - Arduino 5V
                    GND - GND
                    TRIG - D9
                    ECHO - D10

4. 모션 인식 센서 연결
 
 모션 인식 센서 : HC-SR501
 연결 방법 : HC-SR501 VCC - Arduino 5V
                    GND - GND
                    OUT - D7

## 센서 데이터 처리 및 LED 제어 로직 통합


## 센서 에러 검출