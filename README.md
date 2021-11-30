# Typescipt React BoilerPlate

Wepack, Typescript, React로 이루어진 보일러 플레이트. 🍳

CRA 대용이며 config를 공부할 목적으로 만들었습니다.

## tsconfig

noImplicitAny: any를 설정시, 해당 변수의 타입이 모호해지기 때문에 정적 타입을 명확하게 해주는 TypeScript의 장점이 없어지게 됨으로 any 타입은 하지 않는 것으로 설정했습니다!

strictNullChecks: null이나 undefined는 엄연히 다른 정의를 가지고 있기 때문에 명확한게 좋다고 생각합니다.

noFallthroughCasesInSwitch: switch문에서 만약 break나 return이 없다면 분명 의도와는 확연히 다른 코드가 나올 것입니다. 따라서 실수 방지를 위해 설정했습니다.

noImplicitReturns: 함수의 Type을 명확하고 철저하게 하기 위해서 설정했습니다.

noImplicitThis: 헷갈릴 수 있는 this를 막고자 설정했습니다.

noPropertyAccessFromIndexSignature: 변수인 [key]를 설정했다면, 불러올 때에도 변수를 통해서 불러오게 해야한다고 생각합니다.

noUncheckedIndexedAccess: 원래는 변수 [key]를 불러오면 해당 value의 type이 변수에 설정되었는데, [key]는 있을 수도 없을 수도 있기 때문에 undefined, 또한 함께 type 반환을 시켜줄 수 있도록 해당 옵션을 설정합니다.

noUnusedLocals: 쓸데없는 변수가 있어서는 안된다고 생각합니다. 이건 메모리 낭비 및 코드 낭비입니다. 😱

noUnusedParameters: 쓸데없는 파라미터 또한, 메모리 낭비 및 코드 낭비! 방지용 입니다.

### Dev용 config

sourceMap: 난독화 되는 코드를 막아줘서 브라우저에서도 디버깅할 수 있게 해줍니다.

extendedDiagnostics: compile시에 시간이 얼마나 걸리는지 측정해주는 option입니다.

## babel config

babel-loader 대신에 ts-loader와 @babel/preset-typescript를 사용하면 추가적인 loader없이 js와 ts 동시에 babel을 적용시킬 수 있다고 합니다.

따라서 .babelrc에 @babel/preset-typescript를 preset으로 등록했습니다.

[ref: ts-loader](https://webpack.js.org/guides/typescript/#loader)

## sourceMap 설정

ts의 sourceMap 설정과 웹팩의 devtool: 'inline-source-map'로 디버깅이 가능합니다.

[webpack과 ts의 sourceMap 설정으로 Debugging하는 방법](https://webpack.js.org/guides/typescript/#source-maps)

# Webpack config

## entry

시작파일은 'src/index.tsx' 입니다.

## htmlTemplate

html Template은 'src/index.html'입니다.

HtmlWebpackPlugin을 사용했습니다. plugin을 참조해주세요!

## output

./dist 라는 디렉토리에 build가 됩니다.

파일 이름은 bundle.js로 나옵니다.

## extensions

import시에 확장자를 붙여주는 것이 번거로우므로 설정했습니다.

.js, .jsx, .ts, .tsx의 확장자를 생략가능합니다.

## module

해당 project에서 사용가능한 파일들을 이곳에서 볼 수 있습니다.

### ts / tsx

TypeScript를 설정했기 때문에 개발중에는 .js를 허용하지 않습니다.

따라서 .ts와 .tsx만 받아들이도록 했습니다.

(ts-loader를 통해 js로 변환되고 bundling됩니다.)

### css와 scss

css와 scss가 가능하도록 했습니다.

### MiniCssExtractPlugin

style-loader 대신에 MiniCssExtractPlugin을 사용했습니다.

MiniCssExtractPlugin을 통해 javascript bundle 파일에 style이 모두 들어가는 것이 아니라,

css 스타일 만을 따로 번들하여 별개의 파일로 만들어 줍니다.

MiniCssExtractPlugin의 장점은 chunk 파일을 통해 caching이 가능하다는 것입니다.

또한, bundle.js의 크기를 줄여주어 로딩속도를 빠르게 해줍니다.

단점은, js와 css는 비동기적으로 불려오기 때문에 js 혼자 있다가 css가 오면 스타일이 되는 깜빡임 현상이 있을 수 있습니다. 용어로는 Flash of Unstyled Content (FOUC) 라고 합니다.

## dev Server

개발을 위해 devServer 설정을 둡니다.

localhost://3000에서 실행되며, 자동으로 브라우저가 열립니다.

# ESLint

간단한 린트를 추가했습니다.

## JavaScript 세팅

airbnb-base 플러그인을 사용했습니다.

## React

eslint-plugin-react에서 제공하는 기본 설정을 사용합니다.

## TypeScript

@typescript-eslint에서 제공하는 기본 설정을 사용합니다.

## 그 외 custom

@typescript-eslint/no-var-requires를 제외합니다. webpack config에서 commonJS의 require를 있는 그대로의 방식으로 사용하기 위해서입니다.

extensions를 제외합니다. webpack에서 설정한 resolve 옵션으로 몇가지 확장자를 무시할 수 있도록 했는데, 이를 활용하기 위해서입니다.
