# webpack_test

## Lazy Loading 

### 개요
코드를 특정 단위로 스플리팅해서 번들링하고 필요할때만 로드되는 방법을 제공한다.

아래 예시에서 실제 import() 구문이 실행되기 직전까지 로드를 미룰수 있다.

```javascript
button.onclick = e => import(/* webpackChunkName: "print" */ './print').then(module => {
    const print = module.default;

    print();
});
```

## 참고자료
https://webpack.js.org/guides/lazy-loading/