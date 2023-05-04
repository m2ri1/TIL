## Why You Should Create Branches?

```
- 여러 명이서 동시에 작업을 할 때에 다른 사람의 작업에 영향을 주거나 받지 않도록 하기 위하여 사용된다.
- 각자의 독립적인 브랜치에서 작업을 한 이후에 한 브랜치로 다시 모을 수 있기때문에 협업에 유리하다.
```

## pull request 란?

```
- 브랜치에서 코드의 변경사항을 다른 브랜치에 병합(merge)하기 위해 다른 공동 작업자들에게 검토받을 수 있는 기능이다.
```

## merge 란?

```
- 브랜치간의 변경된 작업 내용을 다른 브랜치로 합치는것이다.
```

_추가_

- git flow의 개념

```
git flow란 브랜치를 사용해서 효율적인 협업을 하기 위한 전략이다
```

```
master : 프로젝트의 메인이 되는 브랜치
develop : 직접 개발을 하는 브랜치로 이 브랜치를 기준으로 각자 작업한 기능들을 합치며 프로젝트를 진행해나간다
feature :기능 단위로 개발하는데에 사용하는 브랜치. 기능 개발이 완료되면 develop 브랜치에 합친다
release : master 브랜치로 배포를 하기 전에 테스트를 위해 사용하는 브랜치
hotfix : master 브랜치로 배포를 하고난 후에 문제가 생겼을 떄 수정을 하는데에 사용하는 브랜치
```

- code review 의 개념과 사용하는 이유

```
코드리뷰란 한 작업자가 작성한 코드를 다른 작업자가 검토하고 더 나은 코드를 짜기 위해 도움을 주는것을 말한다
이를 통해 서로의 작업에 도움을 주고받고 유지보수를 비교적 쉽게 할 수 있다
```

- branch rule 의 개념과 사용하는 이유

```
브랜치를 사용하여 협업을 할 때에 작업자들 간의 혼동을 방지하기 위해 지정하여 사용하는 룰을 말한다
```