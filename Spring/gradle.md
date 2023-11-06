## Gradle 이란?

프로젝트의 의존성, 빌드 프로세스, 테스트 실행 및 배포에 관한 정보를 포함하여 관리할 수 있도록 하는 build tool

> 빌드 스크립트를 Groovy 또는 Kotlin 언어로 작성하여 개발자가 더욱 효율적으로 프로젝트를 관리할 수 있게 한다
> build를 한다는것은 즉 빌드의 대상이 되는 모든 빌드 스크립트를 실행한다는 것이다

Gradle의 구조

- 모든 프로젝트는 하나 이상의 task로 구성된다
  > 각각 의존성을 주입하는 등 작업할 수 있게 하는 최소단위

```
rootProject
    ㄴ build.gradle
    ㄴ settings.gradle

    ㄴ subProject01
        ㄴ build.gradle
        ㄴ settings.gradle
        ㄴ ...

    ㄴ subProject02
        ㄴ build.gradle
        ㄴ settings.gradle
        ㄴ ...
```

`settings.gradle` 프로젝트의 설정 파일로, 서브 프로젝트 및 그들의 관계를 정의하는 파일  
`build.gradle` 각 서브 프로젝트와 최상위 프로젝트에 대한 빌드 스크립트를 작성하는 파일

---

#### build.gradle의 implementation, api?

두 키워드는 모두 build.gradle 파일에서 라이브러리를 프로젝트에 주입시키는 키워드이다

`implementation`  
implementation 키워드를 통해 라이브러리를 주입받으면, 해당 모듈에 의존하는 모듈에서는 사용할 수 없다

`api`  
api 키워드를 통해 주입받은 라이브러리는, 해당 프로젝트에 의존하는 다른 프로젝트에 자동으로 적용되어 사용할 수 있다
