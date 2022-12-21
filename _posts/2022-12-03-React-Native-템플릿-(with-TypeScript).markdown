<aside>
🗣 새로운 프로젝트를 위한 템플릿을 만드는 과정을 정리했습니다.
</aside>

## 1. 프로젝트 생성

### 💻 Expo를 이용해서 React Native 프로젝트를 생성합니다.

{% highlight bash %}
npx create-expo-app --template
{% endhighlight %}

TypeScript와 react-navigation을 이용한 몇 개의 예시 스크린과 탭을 포함한 템플릿 옵션을 선택 후 프로젝트 이름을 입력합니다.

### 👩‍💻 실행 방법

{% highlight bash %}
npx expo start
i # iOS
a # android
{% endhighlight %}


## 2. ESLint, Prettier 설정

높은 코드 퀄리티와 원활한 협업을 위한 일관적인 코드 스타일을 위한 도구 두 가지를 추가합니다.

### ✅ 관련 라이브러리와 플러그인을 설치합니다.


{% highlight bash %}
npm install --save-dev eslint @typescript-eslint/eslint-plugin @typescript-eslint/parser
npm install --save-dev eslint-plugin-react@latest eslint-plugin-react-native@latest
{% endhighlight %}

{% highlight bash %}
npm install --save-dev prettier eslint-config-prettier eslint-plugin-prettier
{% endhighlight %}

### ✅ root 디렉토리에 ESLint 설정을 위한 `.eslintrc.js` 파일을추가합니다.

{% highlight jsx %}
module.exports = {
env: {
browser: true,
es2021: true,
node: true,
},
extends: [
'eslint:recommended',
'plugin:prettier/recommended',
'plugin:react/recommended',
'plugin:@typescript-eslint/recommended',
],
overrides: [],
parser: '@typescript-eslint/parser',
parserOptions: {
ecmaVersion: 'latest',
sourceType: 'module',
},
plugins: ['react', 'react-native', '@typescript-eslint'],
rules: {
'eslint-comments/no-unlimited-disable': 0,
'eslint-comments/no-unused-disable': 0,
'react/no-unescaped-entities': 0,
'@typescript-eslint/no-namespace': 0,
'react/react-in-jsx-scope': 'off',
},
};
{% endhighlight %}

### ✅ root 디렉토리에 Prettier 설정을 위한 `.prettierrc.js` 파일을 추가합니다.

{% highlight jsx%}
module.exports = {
// 문자열은 홀따옴표(')
singleQuote: true,
// 코드 마지막에 세미콜론 추가
semi: true,
// 탭 대신 스페이스바 사용
useTabs: false,
// 들여쓰기 너비
tabWidth: 2,
// 후행 콤마 가능한 곳에 모두 사용
trailingComma: 'all',
// 코드 한줄 maximum 너비
printWidth: 80,
// 화살표 함수가 하나의 매개변수를 받을 때 괄호를 생략
arrowParens: 'avoid',
// EoF 방식, OS 별로 처리 방식이 다름
endOfLine: 'auto',
};
{% endhighlight %}

### ✅ package.json scripts에 아래 내용을 추가합니다.

{% highlight json %}
"lint": "tsc --noEmit && eslint --ext .js,.jsx,.ts,.tsx ./",
"lint:fix": "eslint --fix '**/*.{ts,tsx,js,jsx}'",
"prettier": "npx prettier --write **/*.{js,jsx,ts,tsx,json} && npx prettier --write *.{js,jsx,ts,tsx,json}"
{% endhighlight %}


### ✅ ESLint 설정이 잘 됐는지 테스트

{% highlight json %}
npm run lint
{% endhighlight %}

### ✅ Prettier는 파일 수정 후 save 할 때마다 적용 되도록 설정합니다.

IntelliJ → Preferences → Languages & Frameworks → Prettier

Run for files 아래 **On save** 체크 박스 선택!

## 3. styled-component 설정

### 💅 styled-components를 설치합니다.


{% highlight bash %}
npm install styled-components
{% endhighlight %}

### 💅 DefinitelyTyped에 등록된 타입 정의를 설치합니다.

DefinitelyTyped는 TypeScript의 타입 검사 인터페이스를 제공하는 리포지터리 서비스로 등록된 타입 정리 내용을 쉽게 내려받아 사용할 수 있습니다. styled-components의 경우 커뮤니티에서 정리한 타입 정의가 등록되어 있습니다.


{% highlight bash %}
npm install --save-dev @types/styled-components @types/styled-components-react-native
{% endhighlight %}

tsconfig에 타입을 정의하는 경우, 아래 예시와 같이 types에 `styled-components-react-native`를 추가합니다.


{% highlight bash %}
"types": ["jest", "styled-components-react-native"],
{% endhighlight %}

### 💅 styled-component Babel 플러그인을 설치합니다.

서버 측 렌더링, 스타일 최소화 및 더 나은 디버깅 환경에 대한 지원이 추가됩니다.

{% highlight bash %}
npm install --save-dev babel-plugin-styled-components
{% endhighlight %}

## 🔗 참고 링크

- [styled-components: API Reference](https://styled-components.com/docs/api#typescript)
- [https://github.com/DefinitelyTyped/DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped
  )

