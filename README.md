# webpack_test

## Caching

### [contenthash]
```javascript
filename : '[name].[contenthash].js',
```
[name]에는 엔트리 포인트의 명칭이 들어갈것이다.
단일 엔트리 포인트 환경에서 디폴트 값은 'main'인듯 하다.

[contenthash] 엔트리 포인트의 내용을 기반으로 한 해시값이 들어가는데, 
빌드할때 내용이 바뀐다면 이 해시값도 바뀌어서 output파일이 생성될 것이다.
내용이 바뀌지 않은채 다시 빌드된다면 이 해시 값은 동일할 것이다.

하지만 실제로 코드상의 변화가 없어도 해시값이 변하는 경우가 있는데 
이것은 Chunk파일 내부에 보일러플레이트(런타임, 메니페스트)를 가지고 있기 때문이다. 

클라이언트(주로 브라우저)에서는 해시값을 보고 캐싱을 할지를 결정하기 때문에
잘 바뀌지 않는것(주로 서드파티 라이브러리)을 따로 chunk로 묶어 배포하는것이 성능상 유리하다.

###  optimization.runtimeChunk 옵션
```javascript
optimization: {
    runtimeChunk: 'single'
}
```
runtimeChunk를 'single'로 설정하면 빌드할때 runtime으로 시작하는 파일이 생성된다.
즉 chunk파일에서 런타임을 분리해낸것이다.

빌드할때마다 변하는 런타임코드를 분리해냄으로써 어플리케이션 코드의 해시값을 유지할 수 있다.

### optimization.splitChunks.cacheGroups 옵션
```javascript
splitChunks : {
    cacheGroups : {
        vender : {
            test : /[\\/]node_modules[\\/]/,
            name : 'venders',
            chunks : 'all'
        }
    }
}
```
optimization.splitChunks.cacheGroups 옵션을 설정함으로써 벤더 파일들을 하나의 chunk파일로 묶을 수 있다.
어플리케이션코드에 비해 적게 변경되는 서드파티 라이브러리 코드를 동일한 해시값으로 유지하기 위함이다.


## 참고자료
https://webpack.js.org/guides/caching/
https://medium.com/@soeunlee/webpack%EC%9D%84-%EC%84%9C%EB%B9%84%EC%8A%A4%EC%97%90-%EC%A0%81%EC%9A%A9%ED%95%B4-%EB%B3%B4%EA%B8%B0-a5ccfec070f3