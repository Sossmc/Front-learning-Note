**总览**

[TOC]

### React是什么？

React 是一个采用声明式，高效而且灵活的用来构建用户界面的框架。



### React项目基本流程

1. 安装nodejs
2. 使用nodejs的npm包安装create-react-app模块
3. 使用creat-react-app模块创建我们的项目
4. 了解控制我们项目运行测试打包的几个命令
5. 通过npm start运行我们的项目
6. 查看生产的项目目录的结构，并了解其作用
7. 开始创建几个我们自己的组件
8. 再次运行我们的项目
9. 开始打包生产环境中需要的代码
10. 将我们的代码部署进入我们的服务器
11. ok,上线了，我们可以让用户正式访问了
12. 维护调试




### React特点

#### 声明式

React 可以非常轻松地创建用户交互界面。为你应用的每一个状态设计简洁的视图，在数据改变时 React 也可以高效地更新渲染界面。

以声明式编写UI，可以让你的代码更加可靠，且方便调试。

#### 组件化

创建好拥有各自状态的组件，再由组件构成更加复杂的界面。

无需再用模版代码，通过使用JavaScript编写的组件你可以更好地传递数据，将应用状态和DOM拆分开来。

#### 一次学习，随处编写

无论你现在正在使用什么技术栈，你都可以随时引入 React 开发新特性。

React 也可以用作开发原生应用的框架 React Native.



### React零碎

#### 状态提升

当你遇到需要同时获取多个子组件数据，或者两个组件之间需要相互通讯的情况时，把子组件的 state 数据提升至其共同的父组件当中保存。之后父组件可以通过 props 将状态数据传递到子组件当中。这样应用当中的状态数据就能够更方便地交流共享了



### 函数式组件

用函数式组件的编写方式就是：

```
const HelloWorld = (props) => {
  const sayHi = (event) => alert('Hello World')
  return (
    <div onClick={sayHi}>Hello World{props.Mar}</div>
  )
}
HelloWorld.defaultProps = {
  Mar : '!'
}
```



### 规范

组件的私有方法都用 `_` 开头，所有事件监听的方法都用 `handle` 开头。把事件监听方法传给组件的时候，属性名用 `on` 开头。例如：

```javascript
<CommentInput onSubmit={this.handleSubmitComment.bind(this)} />
```

这样统一规范处理事件命名会给我们带来语义化组件的好处，监听（`on`）`CommentInput` 的 `Submit` 事件，并且交给 `this` 去处理（`handle`）。这种规范在多人协作的时候也会非常方便。

另外，组件的内容编写顺序如下：

> 1. static 开头的类属性，如 `defaultProps`、`propTypes`。
> 2. 构造函数，`constructor`。
> 3. getter/setter（还不了解的同学可以暂时忽略）。
> 4. 组件生命周期。
> 5. `_` 开头的私有方法。
> 6. 事件监听方法，`handle*`。
> 7. 
> 8. `render*`开头的方法，有时候 `render()` 方法里面的内容会分开到不同函数里面进行，这些函数都以 `render*` 开头。
> 9. `render()` 方法。

如果所有的组件都按这种顺序来编写，那么维护起来就会方便很多，多人协作的时候别人理解代码也会一目了然。

