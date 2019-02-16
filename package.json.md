###  一、初步理解

​	什么是Node.js的模块（Module）？在Node.js中，模块是一个库或框架，也是一个Node.js项目。Node.js项目遵循模块化的架构，当我们创建了一个Node.js项目，意味着创建了一个模块，这个模块的描述文件，被称为package.json。
​       通常情况下package.json内容出错，会导致项目出现bug，甚至阻止项目的运行。

1. npm安装package.json时  直接转到当前项目目录下用命令npm install 或npm install --save-dev安装即可，自动将package.json中的模块安装到node-modules文件夹下
2. package.json 中添加中文注释会编译出错  
3.  每个项目的根目录下面，一般都有一个package.json文件，定义了这个项目所需要的各种模块，以及项目的配置信息（比如名称、版本、许可证等元数据）。npm install 命令根据这个配置文件，自动下载所需的模块，也就是配置项目所需的运行和开发环境。
4. package.json文件可以手工编写，也可以使用**npm init**命令自动生成。

>  注意：npm init 时，用户需回答一些问题，然后在当前目录生成一个基本的package.json文件。所有问题之中，只有项目名称（name）和项目版本（version）是必填的，其他都是选填的。

### 二、进一步理解

根据常见的node包，根据可以初步得出以下对应关系

> ​    **name** - 包名.
> ​    **version** - 包的版本号。
> ​    **description** - 包的描述。
> ​    **homepage** - 包的官网URL。
> ​    **author** - 包的作者，它的值是你在https://npmjs.org网站的有效账户名，遵循“账户名<邮件>”的规则
> ​    **contributors** - 包的其他贡献者。
>
> ​    **dependencies / devDependencies** - 生产/开发环境依赖包列表。它们将会被安装在 node_module 目录下。
> ​    **repository** - 包代码的Repo信息，包括type和URL，type可以是git或svn，URL则是包的Repo地址。
> ​    **main** - main 字段指定了程序的主入口文件，require('moduleName') 就会加载这个文件。这个字段的默认值是模块根目录下面的 index.js。
> ​    **keywords** - 关键字

以下是根据 创建vue项目的时候 npm init自动生成的package.json做详细的理解

1.下面是最简单的的一个package.json 文件（只有两个数据，项目名称和项目版本，他们都是必须的，如果没有就无法install）

```json
{
  "name": "kocla_test",
  "version": "1.0.0",
}
```

#### 2.scripts字段

指定了运行脚本命令的npm命令行缩写，比如start指定了运行npm run start时，所要执行的命令。

下面的设置指定了npm run dev、npm run bulid、npm run unit、npm run test*、npm run lint*时，所要执行的命令。　

```json
"scripts": {
    "dev": "node build/dev-server.js",
    "build": "node build/build.js",
    "unit": "cross-env BABEL_ENV=test karma start test/unit/karma.conf.js --single-run",
    "test": "npm run unit",
    "lint": "eslint --ext .js,.vue src test/unit/specs"
  },
```

#### 3.dependencies，devDependencies字段

dependencies和devDependencies两项，分别指定了项目运行所依赖的模块、项目开发所需要的模块。它们都指向一个对象，该对象的各个成员，分别由模块名和对应的版本要去组成，表示依赖的模块及其版本范围

--save参数表示将该模块写入dependencies属性，
--save-dev表示将该模块写入devDependencies属性。

```json
"dependencies": {
    "vue": "^2.2.2",
    "vue-router": "^2.2.0"
  },
  "devDependencies": {
    "autoprefixer": "^6.7.2",
    "babel-core": "^6.22.1",
    "babel-eslint": "^7.1.1",
    "babel-loader": "^6.2.10",
    "babel-plugin-transform-runtime": "^6.22.0",
    "babel-preset-env": "^1.2.1",
    "babel-preset-stage-2": "^6.22.0",
    "babel-register": "^6.22.0",
    "chalk": "^1.1.3",
}
```

#### 4、config字段

config字段用于向环境变量输出值。

```json
{ 
  "name" : "foo", 
  "config" : { "port" : "8080" }, 
  "scripts" : { "start" : "node server.js" } 
}
```

#### 5.engines 字段

指明了该项目所需要的node.js版本

```json
"engines": {
   "node": ">= 4.0.0",
   "npm": ">= 3.0.0"
 },
```

#### 6.bin字段

许多包有一个或多个可执行文件希望被安装到系统路径。在npm下要这么做非常容易(事实上，npm就是这么运行的)。

这需要在你的package.json中提供一个bin字段，它是一个命令名和本地文件名的映射。在安装时，如果是全局安装，npm将会使用符号链接把这些文件链接到prefix/bin，如果是本地安装，会链接到./node_modules/.bin/。

比如，要使用myapp作为命令时可以这么做：

```json
{ "bin" : { "myapp" : "./cli.js" } }
```

这么一来，当你安装myapp，npm会从cli.js文件创建一个到/usr/local/bin/myapp的符号链接(这使你可以直接在命令行执行myapp)。



### Tips

对于依赖的包版本，可以前往https://npmjs.org查看包的版本

^X.Y.Z可以对包的版本范围作限定