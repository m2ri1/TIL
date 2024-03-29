#### HTTP의 상태코드

_상태코드란?_

```
- 클라이언트가 보낸 HTTP요청에 대한 서버의 응답코드로 특정 요청의 처리에 대한 작업 수행상태, 또는 성공/실패 여부를 알려준다

- 상태코드의 종류는 크게 5개의 그룹으로 나누어 설명할 수 있다
```

_쉽게 말해, 프론트엔드와 백엔드 사이에서의 명확한 통신을 하기 위해 사용하는 것이다_

---

#### HTTP 상태코드의 종류는 다음과 같다

```
1xx [정보]
    서버가 요청을 받았으며, 연결된 클라이언트에서 작업을 계속 진행하라는 의미
    현재 HTTP 1.0에서는 지원되지 않음
```

> `100` 계속  
> `101` 프로토콜 전환  
> `102` 처리

```
2xx [성공]
    요청을 성공적으로 받았으며, 정상적으로 인식하고 수행하였다는 의미
```

> `200` 성공  
> `201` 작성됨  
> `202` 허용됨  
> `203` 신뢰할 수 없는 정보  
> `204` 콘텐츠 없음  
> `205` 콘텐츠 재설정  
> `206` 일부 콘텐츠  
> `207` 다중 상태  
> `208` 이미 보고됨  
> `226` IM Used

```
3xx [리다이렉션]
    요청 완료를 위해 추가적으로 작업조치가 필요하다는 의미
```

> `300` 여러 선택항목  
> `301` 영구 이동  
> `302` 임시 이동  
> `303` 기타 위치 보기  
> `304` 수정되지 않음  
> `305` 프록시 사용  
> `307` 임시 리다이렉션  
> `308` 영구 리다이렉션

```
4xx [클라이언트 오류]
     클라이언트가 서버에게 보낸 요청이 잘못된 경우
     잘못된 문법으로 인해 서버가 요청을 이해할 수 없음
```

> `400` 잘못된 요청  
> `401` 권한 없음  
> `402` 결제 필요  
> `403` 금지됨  
> `404` 찾을 수 없음  
> `405` 허용되지 않는 메소드  
> `406` 허용되지 않음  
> `407` 프록시 인증 필요  
> `408` 요청 시간초과  
> `409` 충돌  
> `410` 사라짐  
> `411` 길이 필요  
> `412` 사전조건 실패  
> `413` 요청 속성이 너무 큼  
> `414` 요청 URI가 너무 긺  
> `415` 지원되지 않는 미디어 유형  
> `416` 처리할 수 없는 요청범위  
> `417` 예상 실패  
> `418` I'm a teapot  
> `420` Enhance Your Calm  
> `422` 처리할 수 없는 엔티티  
> `423` 잠김  
> `424` 실패된 의존성  
> `424` 메쏘드 실패  
> `425` 정렬되지 않은 컬렉션  
> `426` 업그레이드 필요  
> `428` 전제조건 필요  
> `429` 너무 많은 요청  
> `431` 요청 헤더 필드가 너무 큼  
> `444` 응답 없음

```
5xx [서버 오류]
    클라이언트가 아닌 서버에서의 처리가 잘못되었음을 의미
    서버가 유효한 요청에 대해 요청 처리에 실패하였음을 의미

```

> `500` 내부 서버 오류  
> `501` 구현되지 않음  
> `502` 불량 게이트웨이  
> `503` 서비스를 사용할 수 없음  
> `504` 게이트웨이 시간초과  
> `505` HTTP 버전이 지원되지 않음  
> `507` 용량 부족  
> `508` 루프 감지됨  
> `509` 대역폭 제한 초과  
> `510` 확장되지 않음  
> `511` 네트워크 인증 필요  
> `520` 알 수 없음  
> `598` 네트워크 읽기 시간초과 오류  
> `599` 네트워크 연결 시간초과 오류
