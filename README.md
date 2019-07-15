### 打包
 - 其他人引用该库时有以下几种用法
ES6 module 引用方式  import library from 'library';
CommonJS引用方式  onst library = require('library');
AMD 引用方式 require(['library'],function(){

})

```
    // 以下方式表示library允许通过以上各种方式引用到
    output:{
        libraryTarget:'umd'
    }
```
 - 通过script标签引用
```
    // 以下方式表示library允许通过以上各种方式引用到
    output:{
        library:'library',
        libraryTarget:'umd'
    }
     <script src='library'></script>
```
 - 在全局this上挂载library，但只支持script标签引入形式
 ```
 output:{
     library:'library',
     libraryTarget:'this'
 }
 ```
 - 不将第三方库如lodash打包到自己的业务库中
 ```
 {
     externals:["lodash"],
 }
 // 引用时
 // import _ from "lodash";
 // import library from "library";

 {
     externals:{
         commonjs:"lodash"
     },
 }
 // 如果外部环境以commonjs形式引用lodash，必须取名为lodash
 ```
 参考文档:documentation->configuration->externals
 - npm 发布，注册后，npm publish，其他人可通过npm install 下载应用