# webpack_test

## Caching

### [contenthash]
```javascript
filename : '[name].[contenthash].js',
```
[name]에는 엔트리 포인트의 명칭이 들어갈것이다.

[contenthash] 엔트리 포인트를 기반으로한 해시값이 들어가는데, 
빌드할때 내용이 바뀐다면 이 해시값도 바뀌어서 output파일이 생성될 것이다.

## 참고자료
https://webpack.js.org/guides/caching/