## Json Web Token

JWT란?

- JSON 방식으로 정보를 전달하는 토큰
- 웹서비스의 로그인 인증 시스템에서 주로 사용된다
- 암호화된 문자열의 형태이다

JWT의 특징

- stateful 해야한다는 세션의 단점을 보완할 수 있다
- 별도의 세션 저장소를 강제하지 않기때문에 stateless하여 확장성이 뛰어나다
- signature를 통해 보안성을 갖추고있다

### JWT의 구조

`Header 헤더`  
토큰의 타입과 사용하는 암호화 알고리즘 정보가 들어있다

- 토큰의 타입
- 사용된 알고리즘의 정보

`Payload 페이로드`  
실제로 전달할 내용이(예: 사용자 ID) 들어있다

- key-value (json) 형태로 저장된다
- 사용자, 토큰에 대한 property를 저장한다
- 암호화가 걸려지 않기때문에 민감한 정보를 담지 않는다

- jwt의 표준 스펙은 아래와 같이 정의되어있다

```
iss 토큰 발급자
sub 토큰 제목
aud 토큰 대상자
exp 토큰 만료 날짜
nbf 토큰 활성 날짜
iat 토큰 발급 시간
jti 토큰 식별자
```

> 이 모두를 꼭 포함해야하는것은 아니다

`Signature 서명`  
헤더와 페이로드를 디코딩 한 값을 합친 다음, 개인 키를 사용하여 암호화 되어있다
-> 이를 통해(your-256-bit-secret, 서버가 가지고있는 개인 키)JWT가 변조되지 않았는지 확인할 수 있다

### Signature을 복호화 하여 사용자 인증을 하는 과정

1. jwt 토큰을 클라이언트로 서버와 요청을 보내고, 동시에 전달한다
2. 서버의 개인 키를 사용해 signature을 복호화 하게 된다. 이때 signature를 복호화 하여 알 수 있는 헤더와 페이로드의 값이 jwt의 헤더와 페이로드의 값과 일치한다면 인증을 허용한다

```
서버의 개인키로만 암호화 할 수 있으므로, 따라서 다른 클라이언트에선 복호화가 불가능하다
-> 보안성을 갖춤
```

---

## Access Token과 Refresh Token

Access Token의 문제점

- 유효기간이 짧은경우 잦은 로그인과 토큰 발급을 필요로 하기때문에 번거롭다
- 유효기간을 길게 할경우 보안에 취약해진다

이러한 문제점을 보완하기 위해 사용되는것이 **Refresh Token**이다

Refresh Token이란, Access Token의 유효기간보다 훨씬 길게 설정해두어
Access Token의 유효기간이 만료될때마다 손쉽게 재발급해줄 수 있도록 하는 토큰

Access Token과 Refresh Token을 통한 사용한 인증, 인가 프로세스

1. 사용자 로그인
2. Access Token과 Refresh Token 발급
3. 발급받은 토큰을 쿠키 등에 저장
4. 요청 헤더에 Access Token을 담아 해당 토큰으로 검사
   > - Access Token 만료 -> Refresh Token을 통해 재발급
   > - Refresh Token 만료 -> Access Token을 통해 재발급
   > - 모두 만료 -> 재로그인을 통해 재발급
5. 로그아웃시 Access Token과 Refresh Token 모두 만료

---

## OAuth (2.0)

**용어 정리**

<img width="987" alt="스크린샷 2023-11-12 오후 6 56 06" src="https://github.com/ONEUS-team/gsmatch-back/assets/127807110/0e0196c0-c732-4a93-93e9-db23263a40d2">

### Resource Owner

`Resource Server`의 리소스를 사용하는 사용자  
즉 `Client`의 서비스를 사용하는 진짜 클라이언트를 뜻한다

### Client

`Resource Owner`의 요청을 받고 `Resource Server`에 접근하여 기능을 하는 서버

### Resource Server

`Resource Owner`의 리소스를 보유한 서버  
보호된 자원을 `Client`에게 호스팅 한다

### Authorization Server

`Client`와 `Resource Server`의 연결과정에서 접근권한을 부여하는 서버  
ex) Access Token 발급
