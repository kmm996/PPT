title: 项目中的前端组件开发
speaker: Vincent Hou
url: https://github.com/frontnode
transition: slide

[slide]

# 项目中的前端组件开发
## SCSS Components
<small>演讲者：[@Vincent Hou](https://github.com/vincenthou)</small>

[slide]

![frontnode](https://avatars1.githubusercontent.com/u/7091908 "frontnode") {:&.flexbox.vcenter}

微博：frontnode

QQ： 2080432723

邮箱： frontnode@126.com

开源地址： https://github.com/frontnode

> Web开发，流程改进，最佳实践，性能优化

[slide]

## 前端组件的结构
----
* 结构：HTML -> DOM {:&.bounceIn}
* 表现：CSS -> LESS, SCSS, Stylus
* 行为：Javascript -> coffeescript, typescript, livescript

[slide]

## 开源解决方案
----
* MVVM框架：angular, vuejs, avalon {:&.zoomIn}
* View: reactjs, **riotjs**
* UI Components: bootstrap, foundation, semantic-ui, amaze-ui, brick
* Future: polymer, web components

[slide]

## 我们的选择
----
* Bootstrap
* Angular ui-bootstrap
* Angular directive
* **SCSS**

[slide]

## 组件和页面的关系
----
* 页面由组件组成，组件在页面上定位
* 页面上只需要定义有哪些组件，以及组件的布局和定位
* 页面上使用栅格化布局组件，根据具体情况适当覆盖布局样式
* 组件的行为和样式应该是内聚的，不会依赖或者破坏页面上的样式
* 相同作用域组件之间通过接口传递数据
* 跨作用域或者层级的组件通过pub/sub传递数据

[slide]

## 合理的结构
----
* 最简单的层次
* 语义化的标签 (不是只有div)
* 合理的拆分和组件抽象

[slide]

### 举个栗子
----
![Sample](http://vdemo.qiniudn.com/dom.png) {:&.flexbox.vcenter}

```html
<div class="messages-wrapper" ng-repeat="message in page.messages">
    <div class="message">
        <div class="avatar">
            <img ng-src="{{message.avatar}}"/>
        </div>
        <div class="body">
            <div class="header">
                <div class="name">
                    <a ng-href="{{message.homepage}}">{{message.username}}</a>
                </div>
                <div class="time">{{message.createdAt}}</div>
            </div>
            <div class="content-wrapper">
                <div class="content">{{message.content}}</div>
            </div>
        </div>
    </div>
</div>
```

Any problems?

[slide]

![Mad](http://vdemo.qiniudn.com/mad.jpg) {:&.flexbox.vcenter}

太复杂啦！{:&.zoomIn}

[slide]

更清晰的结构

```html
<ul class="messages-wrapper" ng-repeat="message in page.messages">
    <li class="msg-box">
        <img class="img" ng-src="{{message.avatar}}"/>
        <div class="body">
            <a class="name" ng-href="{{message.homepage}}">{{message.username}}</a>
            <time class="time">{{message.createdAt|date:'yyyy-MM-dd HH:mm:ss'}}</time>
            <p class="content">{{message.content}}</p>
        </div>
    </li>
</ul>
```

[slide]

## 干净的样式
----
* 最少层次的嵌套(5层以内)
* 局部化变量, 防止污染全局空间
* 合理使用mixin和extend
* 适时的重构样式, 提取公共组件

..scss 最佳实践..

[slide]

## 清晰的行为
----
* 最小依赖，仅仅注入需要service, factory, value
* 使用面向对象的思维编写页面和组件
* 适时抽取公共的service，避免DRY
* 避免依赖scope的层次结构传递数据

..展开讨论..

[slide]

## 来个组件
----
* 理解directive, filter, service 和 controller的分工

..组件的最佳实践..

---Last---
[slide]

## 使用lint帮助你学习最佳实践

[slide]

## 好书推荐

程序员修炼之道－从小工到专家
