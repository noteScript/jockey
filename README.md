# JockeyJS Bower

Bower wrapper for JockeyJs.

## Notice

This repo is a fork of `JockeyJS/js` path of [https://github.com/tcoulter/jockeyjs/](https://github.com/tcoulter/jockeyjs/).

Thanks to author [Tim Coulter](https://github.com/tcoulter).

## Contribute

You may make pull requests to this repo or the original one.

## 扩展方法

```javascript
import jockey from '~/jockey.js';

jockey.send('test', {msg: 'hello'}, () => alert('完成执行'), payload => {
  console.log(payload)
})
```

上述方法中最后一个函数是本次发送后的回调方法，依赖APP端使用对应的send('test')方法后，将执行该方法。

但需要注意的是：原jockey中的on方法是一个mixin模式的设计，即可以多个地方执行，你提供的回调方法将始终只会执行一次。

### 扩展步骤

使用jockey.send方法后将自动注册一个同event名字的on事件，事件中的方法就是上述实例中参数为payload的回调函数，执行该方法之前就会调用jockey的off方法关闭已注册的相关事务，直到你再次发起该事件请求。
