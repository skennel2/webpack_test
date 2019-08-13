# webpack_test

## Code Splitting (Dynamic Import)

### import() 함수
```javascript
    return import(/* webpackChunkName: "print" */'./print').then(({default : func})=>{
        /// some codes
    });
```
Promise를 리턴하는 import(사용하려는 모듈 경로)구문으로 동적으로 모듈을 불러올수 있다. 
/* webpackChunkName: "chunk명" */ 주석을 넣어주면 동적으로 로딩될 모듈을 새로운 chunk파일로 분리한다.

## 참고자료
https://webpack.js.org/guides/code-splitting/
https://www.zerocho.com/category/Webpack/post/58ad4c9d1136440018ba44e7