# Typescipt React BoilerPlate

Wepack, Typescript, React로 이루어진 보일러 플레이트. CRA를 사용하면 안되는 기업들에 사용할 수 있다.

매번 똑같은 귀찮은 작업에 힘빼지말자.

개발자잖아?

## tsconfig

noImplicitAny: any를 설정시, 해당 변수의 타입이 모호해지기 때문에 정적 타입을 명확하게 해주는 TypeScript의 장점이 없어지게 됨으로 any 타입은 하지 않는 것으로!

strictNullChecks: null이나 undefined는 엄연히 다른 정의를 가지고 있기 때문에 명확한게 좋다고 생각한다.

noFallthroughCasesInSwitch: switch문에서 만약 break나 return이 없다면 분명 의도와는 확연히 다른 코드가 나올 것이다. 실수 방지를 위해 설정

noImplicitReturns: 함수의 Type을 명확하고 철저하게 하기 위해서 설정

noImplicitThis: 헷갈릴 수 있는 this를 막고자 설정

noPropertyAccessFromIndexSignature: 변수인 [key]를 설정했다면, 불러올 때에도 변수를 통해서 불러오게 해야한다고 생각한다.

noUncheckedIndexedAccess: 원래는 변수 [key]를 불러오면 해당 value의 type이 변수에 설정되었는데, [key]는 있을 수도 없을 수도 있기 때문에 undefined 또한 함께 type 반환을 시켜줄 수 있도록 해당 옵션 설정

noUnusedLocals: 쓸데없는 변수가 있어서는 안된다고 생각. 메모리 낭비 및 코드 낭비이다.

noUnusedParameters: 쓸데없는 파라미터 또한, 메모리 낭비 및 코드 낭비!

### Dev용 config

sourceMap: 난독화 되는 코드를 막아줘서 브라우저에서도 디버깅할 수 있게 해준다.

extendedDiagnostics: compile시에 시간이 얼마나 걸리는지 측정해준다.

## babel config

babel-loader 대신에 ts-loader와 @babel/preset-typescript를 사용하면 추가적인 loader없이 js와 ts 동시에 babel을 적용시킬 수 있다고 한다.

따라서 .babelrc에 @babel/preset-typescript를 preset으로 등록했다.

[ref: ts-loader](https://webpack.js.org/guides/typescript/#loader)

## sourceMap 설정

ts의 sourceMap 설정과 웹팩의 devtool: 'inline-source-map'로 디버깅이 가능하다.

[webpack과 ts의 sourceMap 설정으로 Debugging하는 방법](https://webpack.js.org/guides/typescript/#source-maps)
