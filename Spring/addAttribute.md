## addAttribute의 사용법

### model

`Controller`에서 생성된 _데이터를 View로 전달할 때_ 사용하는 객체

### addAttribute

`model` 객체를 이용하여 전달하기 위해 사용

---

#### addAttribute의 사용법

```
addAttribute(String name, Object value)
```

- value 객체를 name 이름으로 추가
- View에서 name으로 지정된 value를 사용

#### 사용 예제

```
@GetMapping("/board/list")
public String boardlist(Model model) {
    model.addAttribute("list", boardService.boardList());

    return "boardlist";
    }
```

- _boardService.boardList() 를 value로 "list"를 name으로 전달_
- _boardList()에서 boardRepository를 활용하여 board객체의 정보 전달_
