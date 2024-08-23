# Node.js란?

- Chrome V8 JavaScript 엔진(자바스크립트 문법해석하고 동작시켜주는 엔진)으로 빌드된 JavaScript 런타임(프로그래밍 언어가 동작하는 환경).

- 자바스크립트는 프로그래밍 언어이고, 이것이 컴퓨터 환경에서도 동작하고, 브라우저에서도 동작을 함.
  **즉, 브라우저의 내용도 제어가능하고, 컴퓨터도 제어 가능함**

- 기본적으로 웹 브라우저에서는 HTML, CSS, JS만 동작을 함.
- 그런데 순수하게 이 세가지 언어들만을 가지고 웹사이트를 만드는 것이 비효율적임.
- 그래서 개발을 하는 로컬 컴퓨터에다가 개발을 도와주는 여러가지 모듈을 설치해 가지고 와서 도움을 받아가며 개발을 해야함.
- 이러한 모듈들은 실제로 브라우저에서 직접적으로 동작할 수 없기 때문에 대표적으로 이 노드 JS환경에서 도움을 받은 내용들을 html, css, js로 변환을 해주어야함.
- 컴퓨터에게 그러한 변환작업을 명령하고 그 명령이 돌아갈 수 있는 환경이 필요함.
- 그래서 우리는 노드 JS 환경에서 javascript라는 프로그래밍 언어로 그러한 변환을 만들어줄 수 있음.
- 즉, html, css, js를 결과로 만들어서 브라우저에서 동작을 시켜주는 개념이 최신 웹 프론트엔드 개발 환경임.

- 그래서 컴퓨터에 node.js를 설치해서 그런 변환작업을 할 수 있는 환경을 만들어주어야함.

# node.js 다운로드

- 검색해서 다운로드 받을 때, LTS(Long Term Supported) 라고 나와있는 것 하나, 그리고 현재 버전(최신 기능)이 있음.
- LTS는 **장기적으로 안정되고 신뢰도가 높은 지원이 보장되는 버전으로, 유지/보수와 보안(서버 운영)에 초점을 맞춰 대부분 사용자에게 추천되는 버전(짝수버전...)**

## nvm(node version manager)

- 맥OS

* [nvm](https://github.com/nvm-sh/nvm "nvm 다운로드") 은 node.js버전을 언제든지 바꿔줄 수 있는 메니저로, 설치 필요!

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
```

---

- windows

* [nvm-windows](https://github.com/coreybutler/nvm-windows?tab=readme-ov-file "nvm 다운로드")

## nvm으로 node.js 버전 설치

- `nvm ls`로 설치된 node.js 버전 확인
- `nvm install <설치할 버전>`으로 원하는 node.js 버전 설치

- `nvm use <사용할 버전>` 으로 사용할 node.js 버전 선언.

- 사용할 node.js 버전이 선언되면, 그 뒤로 `node`라는 코드를 쓸 수 있음

- `node --version`으로 현재 설치되어있는 노드 버전 확인 가능

- 여러 사람들과 협업하면서 노드 버전이 다르면 영향을 줄 수 있기 때문에 nvm으로 노드 버전관리 하는 것이 중요.

- 더이상 사용하지 않은 버전을 지우고 싶을 때, `nvm uninstall <버전 이름>` 사용하면됨.

- `nvm --help`로 보고 싶은 관련정보 볼 수 있음.

# npm(Node Package Manager)

- **전 세계의 개발자들이 만든 다양한 기능(패키지, 모듈)들을 관리**

* 상당히 많은 패키지들이 있고, `npm install <패키지 이름>`으로 언제든지 사용하고자 하는 패키지, 기능을 설치해서 사용 가능.

---

- **trade-off**(상충관계): npm으로 다양한 기능쓰면서 복잡해짐. 하지만 관리효율 증가, 손쉬운 기능 고도화 등의 장점이 있음.

---

- `npm init -y`
  - node.js 프로젝트를 초기화하고, 기본 설정으로 package.json파일을 자동으로 생성하는 명령어.
  - `npm init`: Node.js 프로젝트를 설정할 때 사용하는 기본 명령어.
  - `-y` : y 플래그는 yes의 약자로, `npm init`이 묻는 모든 질문에 대해 기본값으로 자동 응답하도록 만든다. 즉, 질문을 하나하나 입력하지 않아도 기본값을 사용해 곧바로 `package.json`파일을 생성할 수 있음.

```json
{
  "name": "nodejs",
  "version": "1.0.0",
  "description": "- Chrome V8 JavaScript 엔진(자바스크립트 문법해석하고 동작시켜주는 엔진)으로 빌드된 JavaScript 런타임(프로그래밍 언어가 동작하는 환경).",

  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

- 이런 모양이 나오는데, main은 내가 만든 코드를 패키지화해서 npm에 업로드할 때 필요한 것임으로, 지워도 됨.

- `npm install parcel-bundler -D` 를 입력하여, 패키지 다운로드 함. 그러면 아래와 같이 devDependencies가 추가됨. 이 부분에는 parcel-bundler 패키지를 다운로드받았다는 것이 보여짐.

```json
{
  "name": "nodejs",
  "version": "1.0.0",
  "description": "- Chrome V8 JavaScript 엔진(자바스크립트 문법해석하고 동작시켜주는 엔진)으로 빌드된 JavaScript 런타임(프로그래밍 언어가 동작하는 환경).",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "parcel-bundler": "^1.12.5"
  }
}
```

- 즉, package.json파일의 devDependencies를 통해 이 프로젝트에 어떤 버전의 패키지들을 사용했는지를 알 수 있음.

* 이번에는 `npm install lodash`를 입력함. 그러면 아래와 같이 코드가 또 추가됨.

```json
{
  "name": "nodejs",
  "version": "1.0.0",
  "description": "- Chrome V8 JavaScript 엔진(자바스크립트 문법해석하고 동작시켜주는 엔진)으로 빌드된 JavaScript 런타임(프로그래밍 언어가 동작하는 환경).",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "parcel-bundler": "^1.12.5"
  },
  "dependencies": {
    "lodash": "^4.17.21"
  }
}
```

- 즉, dependencies로 다운로드한 패키지 볼 수 있음.

* 추가적으로 _만약에 설치되었던 node_modules 폴더가 삭제되었다면??_, 그래도 package.json파일에 다운로드했던 패키지와 그 버전이름이 내역으로 남아있기 때문에, **터미널에 `npm install` 혹은 `npm i`를 입력하면 자동으로 devDependencies와 dependecies의 내용을 참고하여 필요한 내용을 설치해줌.**

## package-lock.json

- package.json에 명시되어있는 그 모듈들이 내부적으로 사용하는 다른 모듈들, 내용들에 대한 정보가 자동으로 package-lock.json으로 들어가게됨.

* **package-lock.json은 package.json과 달리 자동으로 관리되는 파일**이라고 생각하면됨.

- **결론적으로, node_modules는 지워져도 되지만, package-lock.json과 package.json파일들은 절대 지워져서는 안됨!**

## 개발용 의존성 패키지 설치 vs 일반 의존성 설치

- `npm install -D xxx`: 개발할 때만 필요한 패키지 설치할 떄 -D 붙임. `-D`는 `--save-dev`의 약자.
  - 패키지가 실제로 웹 브라우저에서 동작하지 않음.(개발할 때만 도움을 받는 용도)
- `npm install xxx`: 패키지가 실제로 웹 브라우저에서 동작해야될 때 사용.

# parcel 패키지 이용해서 open with live server 대신에 웹페이지 브라우저 창에 띄워보기

- parcel-bundler는 웹 애플리케이션을 개발 시 사용하는 모듈 번들러.
- 모듈 번들러는 여러개의 파일(js, css, html, 이미지 등)을 하나의 파일 또는 여러개의 작은 파일로 병합해주는 도구.
- 이렇게 파일을 병합함으로서 애플리케이션 배포 시 필요한 파일을 최소화하고, 네트워크 요청 줄일 수 있음.
- 핫 모듈 리플레이스먼트(HMR): 개발 중 파일 변경되면, Parcel은 브라우저를 자동으로 새로 고침없이 변경된 부분만 즉시 업데이트 가능.
- Parcel은 Babel, PostCSS, UglifyJS 등과 같은 도구들을 자동으로 사용하여 최신 JS코드와 CSS를 구형 브라우저에서도 호환 가능하도록 변환해줌.
- 또한 Parcel은 JS, CSS, Html 뿐 아니라 이미지, 폰트, typescript, Sass, Less 등 다양한 파일 형식 지원.

---

- 원래 package.json 파일 열어보면 script 부분 코드는 이렇게 생겼음.(기본값)

```json
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```

- 위에 내용은 `npm test`를 실행하면 test 스크립트가 실행됨. `echo` 명령어로 내용대로 "Error: no test specified"라는 메세지가 터미널에 출력됨. 그리고 스크립트가 종료코드 1로 종료되면서 `npm test` 명령어는 실패로 간주됨.

- 이제 이부분을 아래와 같이 바꿈.

```json
  "scripts": {
    "dev": "parcel index.html"
  },
```

- **사용자 정의 명령어를 정의하는 곳인 scripts**에 위와 같이 내용을 입력하면, 그러면 parcel index.html이 현재 프로젝트에서만 동작하게됨.

- parcel-bundler라는 패키지에서 개발 서버를 열어서 프로젝트 코드를 동작시켜주는 기능이 있음. 하지만 이 패키지는 어디까지나 우리 프로젝트에서만 설치되어진 것이기 때문에 터미널에서 코드를 직접적으로 실행시킬 수 없음. 그러나 script에 직접적으로 명령을 추가하게되면, 우리 프로젝트 내부에서 명령어가 실행될 수 있도록 인식시켜줄 수 있음. 대신 그 명령어를 여기서는 dev라고 설정함.

- 참고로 명령어 이름은 dev말고 abc, efg 등 원하는 대로 작성하면되는데 대신 터미널에는 `npm run <script에 설정한 명령어 이름>`으로 입력해야함.

- 정리
  - **scripts:** package.json 파일에서 scripts 섹션은 사용자 정의 명령어를 정의하는 곳. 여기에 정의된 스크립트는 터미널에서 npm run <script-name>을 실행하여 호출할 수 있음. 보통은 **dev**라는 이름을 많이 씀.
  - **parcel index.html**: 이 부분은 dev 스크립트가 실행될 때 실제로 실행되는 명령어. parcel은 Parcel 번들러를 실행하는 명령어. index.html은 Parcel이 번들링을 시작할 때 기준이 되는 파일. Parcel은 이 파일을 분석하여, 여기에 포함된 모든 자바스크립트, CSS, 이미지 등 다른 파일들을 찾아서 번들링함.

---

## parcel index.html VS parcel build index.html

```json
  "scripts": {
    "dev": "parcel index.html",
    "build": "parcel build index.html"
  },
```

1. "dev": "parcel index.html"

- 목적: **개발 모드**에서 애플리케이션을 실행.
- 개발 서버가 시작됨. HMR를 통해 코드 변경될 때마다 자동으로 변경사항을 브라우저에 반영함.
- 빠른 빌드와 실시간 피드백 덕에 개발자가 효율적으로 어플리케이션 개발 가능.
- 소스맵 포함되어있어서 디버깅 용이.
- 로컬 호스트(localhost:1234 등)와 같은 URL로 개발 중인 어플리케이션 확인 가능.

2. "build": "parcel build index.html"

- 목적: **배포용으로 애플리케이션을 빌드.(사용자 위함.)**
- Parcel은 프로젝트 파일들을 최적화하여 프로덕션(배포) 용으로 번들링함.
- 여기에는 코드 압축, 트리 셰이킹(Tree Shaking) (사용하지 않는 코드를 제거), 이미지 및 자산의 최적화 등의 작업이 포함.
- 결과물은 dist 폴더(기본값)에 생성되며, 이 폴더의 파일들을 서버에 배포가능.
- 소스맵이 제거되거나 프로덕션 환경에 맞게 최적화됨. 그리고 이 최적화된 파일들을 dist 폴더에 생성.

  - 생성된 dist 폴더를 보면 index.html이 읽기 어렵게 한줄로 보여짐. 이렇게 **작성된 코드를 읽기 어렵게 만드는 작업을 난독화라고하고, 빌드된 결과(제품)는 브라우저에서 해석되는 용도로, 용량을 축소하고, 읽기 어렵게 만드는 등의 최적화를 거치는 것이 좋음.**
  - Bundle : _번들은 우리가 프로젝트 개발에 사용한 여러 모듈(패키지)을 하나로 묶어내는 작업_
  - 즉, 이렇게 개발할 때만 쓰기 때문에, parcel-bundler 설치시 -D 붙임.

# 유의적 버전(Semantic Versioning, SemVer)

- `node --version`, `npm --version` 등 버전 확인 시 세가지의 숫자가 표시되는데 이것의 형태는 **Major.Minor.Patch**이다. (ex) 12.14.1

  - Major: 기존 버전과 호환되지 않는 새로운 버전!
  - Minor: 기존 버전과 호환되는 새로운 기능이 추가된 버전!
  - Patch: 기존 버전과 호환되는 버그 및 오타 등이 수정된 버전!
  - 간혹 ^Major.Minor.Patch (^12.14.1)와 같은 형태로 캐럿(^) 기호가 붙기도함 : _Major 버전 안에서 가장 최신 버전으로 업데이트 가능_

  ```json
    "devDependencies": {
    "parcel-bundler": "^1.12.5"
  },
  "dependencies": {
    "lodash": "^4.17.21"
  }
  ```

  - `npm info lodash`를 입력해서 보면, latest 버전을 알 수 있음.(현재 4.17.21). 하지만, 위에 코드에서 lodash 가 최신버전으로 보여지지만, 실제로 설치되어있는 버전은 최신이 아닐 수도 있음.
  - 어떻게 설치된 버전이 최신인지 아닌지 알 수 있는가???
    - node_modules 폴더 들어가서, lodash 폴더 찾고, 그 안에서 package.json파일 확인!
    ```json
      "name": "lodash",
      "version": "4.17.21",
    ```
    - package.json의 version 부분에서 latest version이 맞는지 확인!

* 만약 특정한 버전을 설치하고 싶다면 패키지이름에 @붙여서 버전 이름 적어서 install하면됨

```bash
npm install lodash@4.17.20
```

- 위 코드 실행시키면, package.json 에 lodash 버전 부분이 변경될 것임.

```json
  "dependencies": {
    "lodash": "^4.17.20"
  }
```

- 다시 최신버전으로 update하고 싶으면 아래 코드 실행.

```bash
npm update lodash
```

- 위에서 말한 것처럼 ^ 캐럿 기호는 언제든, major 버전 안에서 minor나 patch가 최신 버전으로 update 될 수 있다는 의미라고 했음.
- 만약에 ^가 버전 앞에 없다면, `npm update <패키지 이름>`의 코드가 실행되어도 자동으로 버전이 major 버전 내에서 최신 버전으로 업데이트가 안됨.
- ^는 개발자가 필요에 따라 지울수도 추가할 수도 있음
  - ^의 장점: 언제든 손쉽게 `npm update`를 통해 최신 minor, patch를 update할 수 있음.
  - 단점: 나는 특정 버전을 써야하는데 의도치않게 새로운 버전으로 업데이트될 수 있음.

# 깃헙에 push 할때!!!

- 버전관리가 따로 필요 없는 폴더들이 있음. 예를 들어, .cache, dist, node_modules 와 같은 친구들... 심지어 이 친구들은 삭제시켜도 됨(언제든, package.json과 package-lock.json파일이 살아있는한 복구 가능.)
  - .cache, dist: `npm run build` 입력하면 복구됨.
  - node_modules: `npm i` 입력하면 복구됨.

* 게다가 node_modules는 용량이 크고, 이것을 깃헙에 올리는데 시간이 오래걸림. 즉, 이 폴더를 깃헙에 올리면 너무 비효율적임.

- **.gitignore** 사용!!: 위와 같은 폴더들을 깃허브에 올리고 싶지 않음으로 파일를 만들어 관리해줄거임.
  - .gitignore 이라는 이름으로 **파일**을 만들고, 거기에 업로드하고 싶지않은 **폴더이름 한줄씩 입력**
  ```git
  .cache/
  dist/
  node_modules/
  ```

* 그 후에 `git init` 입력하고 이후 과정 실행해주면 됨!

# 패키지 버전 일치시키기

- 간혹 다른 프로젝트를 클론 코딩할 때 사용했던 패키지 버전이랑 내가 사용하는 버전이 다를 수 있음. 이런 문제점을 해결하려면 package.json, package-lock.json파일을 다운로드하여 이용하면 문제되지 않음.

  - 특히, 깃헙에서 코드 가져오는 경우. github에서 가져오고자하는 파일 클릭하고, raw 버튼을 눌러 새창에 띄운 후 확인이 가능한 디렉토리에 저장하고 사용하는 editor에 파일 열어주면 됨.

- package-lock.json은 현재 설치된 모든 외부 모듈의 버전을 트리 구조(필요한 모듈들이 연결, 연결, 연결되어있음...)로 명시함. 그래서 package.json뿐만 아니라 package-lock.json 파일도 필요!!

- 가져온 두 파일을 기반으로 `npm i`를 이용해 node_modules 폴더 얻기~~
