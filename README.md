# cordovaVueForDataEE
主要文档结构图
```
cordovaApp
|
│  config.xml //cordova配置文件
|
│  package.json // cordova的npm包信息文件
│  
├─node_modules //cordova的npm包
│
├─platforms //cordova平台相关文件
│
├─plugins //cordova插件
│              
├─www //vue构建后的文件，cordova会把里面的内容打包成app
|
├─vue-src //vue 源码文件
│  │  .babelrc //babel配置文件
│  │  .editorconfig 
│  │  .gitignore 
│  │  .postcssrc.js
│  │  index.html //html源文件
│  │  package-lock.json 
│  │  package.json //vue的npm包信息文件
│  │  
│  ├─build //vue的构建相关webpack配置文件
│  │      build.js
│  │      check-versions.js
│  │      logo.png
│  │      utils.js
│  │      vue-loader.conf.js
│  │      webpack.base.conf.js
│  │      webpack.dev.conf.js
│  │      webpack.prod.conf.js
│  │      
│  ├─config //vue配置文件
│  │      dev.env.js
│  │      index.js
│  │      prod.env.js
│  │      
│  ├─node_modules //npm包文件
│  ├─src //源码文件
│  │  │  App.vue
│  │  │  main.js
│  │  │  
│  │  ├─assets 
│  │  │      logo.png
│  │  │      
│  │  ├─components
│  │  │      HelloWorld.vue
│  │  │      
│  │  └─router
│  │          index.js
```
在搭建好android开发环境之后，全局安装cordova，我的cordova版本是8.0,尽量与我一致。另外[这里](https://cordova.apache.org/#getstarted)是cordova的官方文档
```
npm install -g cordova
```
在项目git clone下来之后，在cordovaApp文件夹下面，新建www目录，新建platforms目录（尽量保证www目录下面有html文件哈，不然因为目录问题可能会出错）
```
执行
npm install
```
来安装cordova的node包
```
执行
cd vue-src
npm install
```
来安装vue的node包
```
执行
cordova platform add android
```
来添加安卓平台
```
手机连上电脑，打开usb调试后执行
cordova run android 进行调试
```
另外也可以添加浏览器平台进行调试，缺点是不能使用一些例如相机的插件
```
cordova platform add browser
cordova run browser
```

业务代码需要写在vue-src中的src文件夹中,在每次需要构建的时候
```
在vue-src文件夹下执行
npm run build
```
这样文件会被放到www文件夹中
```
在cordovaApp文件夹下
执行cordova run android
或者cordova run browser
进行调试
```

如果需要构建
```
执行
cordova build android
app文件存放在
/platforms/android/app/build/outputs/apk/debug/app-debug.apk 文件夹下
```