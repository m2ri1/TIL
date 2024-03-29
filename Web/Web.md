## 웹 개발자 직군 정리

### 프론트엔드 개발자

```
웹의 개발 영역중, 사용자들이 직접 눈으로 보는 화면(UI)을 구성하고 기능을 구현한다 (버튼, 애니메이션, 입력창 등의 화면 구성을 말한다)
HTML, CSS, JS등의 언어를 사용한다
```

### 백엔드 개발자

```
사용자의 정보들을 웹 페이지의 프론트에서 받아들이고 관리한다
또는 그런 정보들을 서버로 전달하고, 저장한다
백엔드 개발자가 되기 위해서 배워야 하는 언어들의 종류는 비교적 다양하다
대표적으로 Java, Python, JavaScript(Node.js)등의 언어를 사용한다
```

### DB(데이터베이스) 개발자

```
대량의 데이터들을 효율적으로 관리하기 위해 일을 한다
데이터베이스 관리시스템을 설계하고 개발한다
```

### 웹 디자이너

```
웹 사이트를 제작하는 과정에서 디자인을 맡는다
사용자들에게 보다 직관적인 인터페이스를 구현하기 위해 노력한다
```

### devOps 엔지니어

```
DevOps 엔지니어는 개발부터 시스템 유지관리에 이르는 프로세스의 전반적인 것들을 자동화 시키고, 관리한다
```

프론트엔드와 백엔드의 차이점

```
프론트엔드와 백엔드는 모두 웹 사이트의 개발자라는 같은 면이 있지만,
프론트엔드 개발자는 우리 눈에 보이는 인터페이스 영역을 개발하고
백엔드 개발자는 사용자가 보지 못하는 환경(서버)을 개발하고 구성하는 일을 한다
```

---

## 내가 하고싶은 전공

백엔드 개발

## 그 이유

서버를 개발하고 관리하는 일을 하는것이 흥미로워보이고, 배우고 싶기 때문이다

---

### 프레임워크 (framework)란?

```
소프트웨어 개발을 할때, 작업을 비교적 일관적이고 유지보수성을 높이며 할 수 있도록 하는 뼈대를 제공하는 툴
```

- 반복적인 작업을 줄이고 코드작성에 필요한 구조를 기본적으로 제공한다

- 코드의 유지보수성을 향상시키고, 보안적으로 안정적인 코드를 짤 수 있다

- 개발자가 기존의 프레임워크를 수정하여 사용할 수도 있고 커뮤니티에서 다른
  개발자들이 공유한 내용을 볼수도 있기때문에 빠른 소프트웨어 개발을 가능하게 한다

### 라이브러리 (library)란?

```
소프트웨어의 구성요소 중 한가지로, 개발 플랫폼에서 컴퓨터가 바로 사용할 수 있는 특정한 기능만을 수행하도록 제작된 함수나 변수등 개발에 필요한 의 집합
```

- 해당 라이브러리의 기능을 호출하거나, 해당 라이브러리의 기능을 실행하는 API를 사용하는 프로그램을 개발하여 기능을 사용할 수 있다

- 대상 환경(플랫폼)에서 바로 실행될 수 있는 형태로 제공된다
  > (프레임워크는 라이브러리를 포함한다)

---

### 프레임워크와 라이브러리의 개념 비교

_공통점은?_

```
프레임워크와 라이브러리는 모두 코드의 재사용성을 높이고 개발 속도를 빠르게 할 수 있도록 도움을 주는 역할을 한다
```

_차이점은?_

```
프레임워크는 이미 규칙이 정해져있는 툴 내에서 개발자가 필요한 코드를 추가로 작성하고, 그 코드들은 프레임워크의 구조를 따라서 실행된다
반면, 라이브러리는 전체 구조가 아닌 특정 기능을 수행하는 역할을 하므로 개발자가 프로그램 내에서 직접 라이브러리의 기능들을 호출하고, 프로그램의 구조는 개발자가 직접 정의하여 사용된다

즉 코드의 전체적인 구조와 흐름을 보았을때 프레임워크를 사용한 경우는 프레임워크의 구조를 기반으로 코드가 돌아가지만 라이브러리는 사용자가 작성한 구조를 따르고, 필요한 경우에 따라서 호출되어 쓰인다
```

### Api(Application Programming Interface) 란?

```
운영 체제나 프로그래밍 언어가 제공하는 기능을 응용 프로그램에서 사용할 수 있도록 하는 인터페이스를 제공하는 도구
```

- 개발하거나 유지 보수할 필요가 없는 외부 데이터와 기능에 접속할 수 있게 해주는 중간 매개체 역할을 한다

  > 이를 이용해 다른 애플리케이션에서 데이터를 가져오거나 저장 또는 수정, 삭제하며 프로그램을 개발할 수 있다

- open api란, 다양한 기업 또는 기관에서 제공하는것으로 해당 기관의 데이터나 서비스를 활용할 수 있도록 공개한 api를 말한다

---

## HTTP란?

#### (HyperText Transfer Protocol)

```
텍스트 기반의 통신 규약으로 인터넷에서 데이터를 주고받을 수 있는 프로토콜이다
```

#### HTTP의 특징

- TCP/ IP를 이용하는 `응용 프로토콜`이다

  > 컴퓨터와 컴퓨터간에 데이터를 전송 할 수 있도록 하는 장치. 인터넷을 통해 원하는 데이터를 주고 받는 기능을 이용하는 응용 프로토콜

- 연결 상태를 유지하지 않는 `비연결성 프로토콜`이다

  > 이러한 단점을 해결하기 위해 Cookie (서버가 사용자의 데이터를 브라우저 측에 저장한 후 추후에 재접속 하였을때 다시 해당 데이터를 받아올 수 있게하는것) 를 사용한다

- `요청 <-> 응답` 방식으로 동작한다

---

#### HTTP의 동작

클라이언트 즉, 사용자가 브라우저를 통해서 어떠한 `서비스를 요청`(request)을 하면 서버에서는 해당 요청사항에 맞는 결과를 찾아서 `사용자에게 응답`(response)하는 형태로 동작한다

- 요청  
  클라이언트 -> 서버
- 응답  
  서버 -> 클라이언트
  > `서버` : 어떠한 자료에 대한 접근을 관리하는 네트워크 상의 시스템

> `클라이언트` : 그 자료에 접근할 수 있는 프로그램, 사용자

> `요청(Request)` : 클라이언트가 서버에게 연락하는 것  
> (요청을 보낼때는 요청에 대한 정보를 담아 서버로 보낸다)

> `응답(Response)` : 서버가 요청에 대한 답변을 클라이언트에게 보내는 것

---

#### HTTP와 HTTPS의 차이점

HTTP의 특징

- 웹사이트에서 정보를 전송하기위한 표준 프로토콜로, 기본적으로 암호화를 하지 않기때문에 보안에 취약하다

HTTPS의 특징

- 마찬가지로 웹 사이트에서 데이터를 전송하는데에 사용되는데, 그 과정에서 암호화를 진행한다는 특징이 있다

- 정보 보호 및 보안에 있어서 굉장히 안전하다
