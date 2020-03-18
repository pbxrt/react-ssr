# React-SSR

## 纯粹SSR、纯粹CSR、和React SSR

## React SSR 原理

### renderToString 方法
组件在服务端渲染后，在浏览器端还会渲染一次，来完成组件的交互等逻辑。渲染时，react在浏览器端会计算出组件的data-react-checksum属性值，如果发现和服务端计算的值一致，则不会进行客户端渲染。所以data-react-checksum属性的作用是为了完成组件的双端对比

### renderToStaticMarkup 方法
将组件渲染为html字符串，不会带有data-react-checksum属性。

### hydrate 方法
从react 16开始，服务端渲染renderToString方法渲染的结果不再有 data-react-* 属性，当然也相应的提供了一个客户端渲染API - ReactDOM.hydrate()，从使用上来说和ReactDOM.render()没有差别

### renderToNodeStream
性能做了改进，提供了可以将组件转换为字节流的renderToNodeStream方法。
renderToNodeStream的性能要好的多，可以有效缩短TTFB时间
因为组件渲染为字符串，是一次性处理完后才开始向浏览器端返回结果。而采用流的话，可以边读边输出，可以要让页面更快的展现，缩短首屏展现时间

### renderToStaticNodeStream


### babel 编译命令
npx babel index.js --out-file index-compiled.js --presets=@babel/preset-react