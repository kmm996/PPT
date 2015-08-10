title: 前端工程化在OmniSocials中的实践
speaker: Vincent Hou
url: https://github.com/vincenthou
transition: move
theme: colors

[slide]

# 前端工程化在OmniSocials中的实践
## Frontend engineering in OmniSocials
<small>演讲者：[@Vincent Hou](https://github.com/vincenthou)</small>

[slide]

## 前端工程化的范围
----
* 代码和开发流程规范
* 文件组织和模块化开发
* 前端组件化开发
* 系统构建工具链
* 前后台集成解决方案
* 前端性能和错误监控
* 自动化测试和持续集成
* 前端安全检测和防范

[slide]

## 代码和开发流程规范
----
* 规范化文档 {:&.zoomIn}
```sh
README.md
javascript-style-guide.md
css-style-guide.md
html-style-guide.md
development-process-guide.md
```
* 工具配置 {:&.zoomIn}
```sh
.editorconfig
.jshintrc
.jshintignore
.jscsrc
coffeelint.json
scsslint.json
```

[slide]

## 文件组织和模块化开发
----
### 基本的文件组织
```sh
.
├── css
├── images
├── index.html
├── js
└── pages
```

[slide]

## 文件组织和模块化开发
----
### 进阶的文件组织
```sh
project
  ├─ component_modules (生态模块目录)
  │  └─ FortAwesome-Font-Awesome
  │      └─ 4.1.0
  │         └─ ...
  ├─ components    (工程模块)
  │  ├─ directive  (directive)
  │  │  └─ more
  │  ├─ filter     (filter)
  │  │  └─ data
  │  ├─ component  (组件)
  │  │  ├─ header
  │  │  └─ footer
  │  └─ page       (页面)
  │     ├─ index
  │     └─ detail
  │         ├─ icon.png
  │         ├─ detail.css
  │         ├─ detail.tpl
  │         └─ detail.js
  ├─ views             (非模块化资源)
  ├─ component.json    (生态依赖描述)
  ├─ ...
```

[slide]

## 文件组织和模块化开发
----
### 模块化和依赖管理工具
* **加载器:** 基于文件, 使用module模式 [labjs](http://labjs.com/), [yepnope](http://yepnopejs.com/)
* **AMD:** 依赖前置, 提前执行 [requirejs](http://requirejs.org/)
* **CMD:** 依赖就近, 延迟执行 [seajs](http://seajs.org)
* **CommonJS:** 同步加载, 更适用于服务器端开发 [CommonJS规范](http://javascript.ruanyifeng.com/nodejs/commonjs.html), [Browserify](http://browserify.org/)
* **Component: ** 依赖资源编译后放到同一个目录中 [Component](https://github.com/componentjs/component), [Duo](http://duojs.org/)
* **对比:** [关于 CommonJS AMD CMD UMD](http://my.oschina.net/felumanman/blog/263330?p=1)

[slide]

## 文件组织和模块化开发
----
### 我们的做法 {:&.slideIn}
* 基于子项目的分文件夹
* 区分核心组件和一般扩展
* 基于扩展搭建独立开发结构
* 静态资源源码和编译代码分离
* 使用requirejs来做依赖管理和异步加载工具

[slide]

## 前端组件化开发
----
### 组件的映射关系
![组件化](http://scrat-team.github.io/public/c/scrat-site/0.1.0/pages/modular/page_1356fae.png)

[slide]

## 前端组件化开发
----
### 组件化开发方案 {:&.bounceIn}
* **通过模式自组织:** [CSS模块化](https://github.com/vincenthou/vincenthou.github.io/issues/25), [JqueryUI widget](http://jqueryui.com/widget/)
* **现成组件库:** [Bootstrap](http://www.bootcss.com/), [Foundation](http://foundation.zurb.com/), [AmazeUI](http://amazeui.org/), [SemanticUI](http://www.semantic-ui.com.cn/)
* **组件化开发框架:** [React](http://facebook.github.io/react/), [Angular Directive](http://facebook.github.io/react/), [VueJS Directive](http://vuejs.org/guide/directives.html), [Polymer](https://github.com/Polymer/polymer), [Brick](http://mozbrick.github.io/), [Web Components](https://github.com/w3c/webcomponents)

[slide]

## 前端组件化开发
----
### 组件和页面的关系 {:&.slideIn}
* 页面由组件组成，组件在页面上定位
* 页面上只需要定义有哪些组件，以及组件的布局和定位
* 页面上使用栅格化布局组件，根据具体情况适当覆盖布局样式
* 组件的行为和样式应该是内聚的，不会依赖或者破坏页面上的样式
* 相同作用域组件之间通过接口传递数据
* 跨作用域或者层级的组件通过pub/sub传递数据

[slide]

## 前端组件化开发
----
## 我们的选择
* Bootstrap
* Angular ui-bootstrap
* Angular directive
* **SCSS**

[More Details](https://github.com/frontnode/PPT/blob/master/ppts/frontend-component-development.md)

[slide]

## 系统构建工具链
----
### 工具的价值
* 根据场景提供便捷化开发方式
* 节省重复人工劳动, 专注于业务开发
* 自动化应用最佳实践规范

[slide]

## 系统构建工具链
----
### 工具的关注点
* 自动化编译流程
* 多平台多语言本地开发环境
* 文件监听和livereload
* 自定义流程
* 模块和组件的管理
* 部署配置
* 前端编译工具 (LESS, SCSS, Stylus, CoffeeScript, TypeScript, ES5/6, Jade, Haml)
* 打包合并资源
* 代码压缩和模糊化
* 图片的合并和压缩
* 后处理器介入
* 基于Hash或者时间的版本控制
* CDN部署和引用替换
...

[slide]

## 系统构建工具链
----
### 可用的工具
* **Yo; Grunt/Gulp: ** [Yeoman](http://yeoman.io/), [Grunt](http://www.gruntjs.net/), [Gulp](http://gulpjs.com/)
* **百度: ** [FIS](http://fis.baidu.com/)
* **UC:** [Scrat](http://scrat-team.github.io/#!/index)
* **去哪儿: ** [Fekit](https://github.com/rinh/fekit)

[slide]

## 系统构建工具链
----
### 我们的做法
* **Yo; Grunt/Gulp: ** [Yeoman](http://yeoman.io/), [Grunt](http://www.gruntjs.net/), [Gulp](http://gulpjs.com/)
* **百度: ** [FIS](http://fis.baidu.com/)
* **UC:** [Scrat](http://scrat-team.github.io/#!/index)
* **去哪儿: ** [Fekit](https://github.com/rinh/fekit)

[slide]

## 参考资料

* [前后端分离的思考与实践](http://ued.taobao.org/blog/2014/04/full-stack-development-with-nodejs/)
* [前端架构那些事儿](http://div.io/topic/442)
* [前端工程之模块化](http://fex.baidu.com/blog/2014/03/fis-module/)
* [研发模式的思考](https://github.com/aralejs/aralejs.org/issues/50)
* [浅谈前端集成解决方案](https://github.com/fouber/blog/issues/1)
* [前端工程与性能优化](https://github.com/fouber/blog/issues/3)
* [前端工程与模块化框架](https://github.com/fouber/blog/issues/4)
* [前端工程与模块化框架](https://github.com/fouber/blog/issues/4)
* [2015前端组件化框架之路](https://github.com/xufei/blog/issues/19)
* [关于前端开发中“模块”和“组件”概念的思考](https://github.com/hax/hax.github.com/issues/21)