## OSI 7계층

### OSI 7계층이란

Open Systems Interconnection Reference Model의 약자로, 컴퓨터 네트워크 프로토콜 디자인과 통신을 계층으로 나누어 설명한 것을 말합니다
7계층 모델은 프로토콜의 기능별로 나누었다는 특징이 있고, 각 계층의 하위 기능만을 이용하여 상위계층에 기능을 제공합니다

```
-------------
7. 응용 계층
-------------
6. 표현 계층
-------------
5. 세션 계층
-------------
4. 전송 계층
-------------
3. 네트워크 계층
-------------
2. 데이터 링크계층
-------------
1. 물리 계층
-------------
```

#### 물리 계층

- 데이터 링크 개체 간의 비트 전송을 위한 물리적 연결을 설정, 유지, 해제 하기 위한 수단을 제공합니다
- 0과1로만 이루어진 비트들을 통해 신호를 주고받는 기능을 합니다  
  -> 케이블, 리피터, 허브 등

#### 데이터 링크계층

- 물리계층에서 송수신된 정보의 오류를 관리하여 정보의 전달을 무사히 수행할 수 있도록 합니다
- 브릿지나 스위치를 통해 맥주소를 가지고 물리계층에서 받은 정보를 전달합니다

#### 네트워크 계층

- 라우팅(데이터를 목적지까지 전달) 기능을 수행하는 계층입니다
- 데이터를 연결하는 다른 네트워크를 통해 전달함으로써 인터넷이 가능하게 만드는 계층입니다

#### 전송 계층

- 사용자들이 신뢰성있는 데이터를 주고 받을 수 있도록 해 주는 계층입니다
- 패킷들의 전송이 유효한지 확인하고 전송 실패한 패킷들을 다시 전송하는 기능을 하는데, 이중 가장 잘 알려진 전송 계층의 예는 TCP입니다(3-way handshaking을 통한 연결 지향성 통신)

#### 세션 계층

- 양 끝단의 프로세스가 통신을 관리하기 위한 방법을 논리적인 연결로 제공하는 계층입니다
- 통신하는 사용자들을 동기화하고 오류복구 명령들을 일괄적으로 다루는 계층입니다
- 통신 중 연결이 끊어지지 않도록 유지시켜주는 역할 수행하기 위해 **TCP/IP 세션 연결의 설정과 해제, 세션 메세지 전송** 등의 기능을 수행합니다

#### 표현계층

- 응용계층으로부터 데이터 표현 형식상의 차이로 생기는 부담을 덜어주기 위해, 하위 계층에서 온 데이터를 사용자가 이해할 수 있는 형태로 만드는 기능을 하는 계층입니다
- 암호화, 복호화 등의 작업을 합니다

#### 응용 계층

- 응용 프로세스와 관계하여 응용서비스를 수행하는 계층입니다
- User Interface를 제공하며 7계층 중 사용자와 가장 밀접한 계층입니다  
  -> 구글 크롬, 파이어폭스, 사파리 등 웹 브라우저와 전자메일 등