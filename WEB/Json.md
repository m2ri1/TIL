## Json이란 무엇인가

#### **Json** (JavaScript Object Notation)

- 데이터를 저장하거나 전송할 때 많이 사용되는 경량의 DATA 교환 형식 (데이터를 표기하는 형식을 뜻함)

- 사람과 기계 모두 이해하기 쉬우며 용량이 작기때문에, XML을 대체하여 많이 사용된다

- 서버와 클라이언트 간의 교류에서 많이 사용된다

---

## JSON 문법

- `null` `number` `string` `array` `object` `boolean`을 사용할 수 있고
  원하는 만큼 중첩시켜서 사용 가능하다
- `key, value`가 존재할 수 있으며 key값이나 문자열은 항상 쌍따옴표를 이용하여 표기한다
- ex) `{ "key" : "value" }`

#### JSON 문법의 예시

```
{
  "firstName": "Park",
  "lastName": "miri",
  "email": "mirimiri@gmail.com"
}
```

```
{
  "students": [
    {
      "name": "kdh",
      "number": "1"
    },
    {
      "name": "kys",
      "number": "2"
    },
    {
      "name": "bjh",
      "number": "3"
    }
  ]
}
```
