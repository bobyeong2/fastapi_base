### fastapi를 사용해본 뒤 기본 폴더를 정리한 내용

init : 2022/10/26

1. 왜 만들었는가?
    - Flask와 비슷하게 micro service제작 시 유연하게 작성할 수 있다는 장점이 있지만, Django처럼 base folder가 없어서 프로젝트 구조는 어떻게 만들어야 하고, 어떻게 파일을 분리해야하는지 등 main.py만 띄우고 무작정 만들기에는 여러가지로 고민해야할 사항이 한 두가지가 아님.

    - Project 구조는 요구사항에 맞게 변할 수 있지만, 처음 개발 시 대략적인 틀을 잡고 요구사항 반영에 더 집중하고 싶다는 생각에 제작하였음.


2. 폴더 별 세부 사항 정리

```

ProjectFolder (project root folder)
|
|--- main.py (fast api 실행 파일)
|
|--- apis --- base.py         (API router를 정의하는 공간 main.py에서 사용됨.)
|           |--- custom files (요구사항에 맞게 api를 작성하는 공간)
|
|--- core                     (Fast API의 주요설정 파일 // 비밀번호 해싱 // access token 등을 하는 공간 )
|
|---  db  ---                 (db에 관련한 파일을 모은 폴더 // session, models, repository, base class를 정의하는 공간)                
|           |--- models       (database model을 정의하는 공간)
|           |--- repository   (db에서 동작하는 함수 -> 예 : 회원가입 / 로그인 등 )
|
|--- schemas                  (Data Validation하는 공간 // 데이터 구조를 정의하고 유효성 검사를 하는 공간)
|
|--- static --                (정적 파일을 모아둔 곳 js, img, css 등)
|            |--- js
|            |--- img
|
|--- templates --              (template를 구현하는 공간 // base 및 기능별로 분리함.)
|               
|
|--- tests ---                 (각종 Test Code를 정의하는 공간)
|
|--- webapps --                (webapp의 router를 정의하고 구현하는 공간)
|
|--- .env                      (DataBase Config file 대개 gitignore로 설정 내용이 보이지 않도록 설정함.)
```

3. 실행

- 해당 파일 clone
```
CMD : git clone {this repository}
```

- requirements.txt에 명시된 패키지 설치
```
pip install -r ./requirements.txt
```

- 파일 실행


```
"--reload" is option -> develop mode


uvicorn main:app --reload
```