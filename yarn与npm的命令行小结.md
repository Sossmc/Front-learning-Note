#### 1 npm参数等

备注：<=> 意为等价于；

1、npm install <=> npm i

     --save   <=> -S     
    
     --save-dev  <=> -D 
    
      npm run start <=> npm start  // 对应"scripts"里的"start"命令
    
      少敲几下键盘，何乐而不为

2、npm i --save-dev  <packname>  

      工程构建（开发时、“打包”时）依赖 ；例：xxx-cli , less-loader , babel-loader...

3、npm i --save <packname> 

      项目（运行时、发布到生产环境时）依赖；例：antd , element,react...

4、对应关系如下（至于我们啥时候用--save、啥时候用--save-dev 感觉是个规范问题，用反了项目一样可以跑起来（对于安装依赖正确时），但会给其他看你项目的人带来误解、可能会导致一些bug的出现，还有一些配置的错乱等）

5、使用 npm i 安装package.json里的依赖时，两部分的包都会pull下来

     5-1、使用 --prod、npm i --prod <=> npm i --production  // 仅会拉取dependencies中的依赖
     5-2、设置NODE_DEV=production时            // 效果同上，仅会拉取dependencies中的依赖 (注意等号两边没空格)
      5-2-1、命令行设置（注意不同环境时的"分割符"）
        window => cmd ：set NODE_ENV=production && xxxx
        mac      => shell  : NODE_ENV=production 空格 xxxx
      5-2-2、package.json=>script命令中设置


彩蛋：在新建package.json文件时，我们可以使用npm init -y 快速创建（yes 表示一路默认创建，还有 -f 表示 force）

#### 2 yarn对比npm

**一、首先需要了解的命令**

​     `npm install` === `yarn` —— install 安装是默认行为。

​     `npm install taco --save` === `yarn add taco` —— taco 包立即被保存到 package.json 中。

​     `npm uninstall taco --save` === `yarn remove taco`

在 npm 中，可以使用 `npm config set save true `设置 — `-save `为默认行为，但这对多数开发者而言并非显而易见的。在 yarn 中，在package.json 中添加（add）和移除（remove）等行为是默认的。

​     `npm install taco --save-dev` === `yarn add taco --dev`

​     `npm update --save` === `yarn upgrade`

update（更新） vs upgrade（升级）， 赞！upgrade 才是实际做的事！版本号提升时，发生的正是upgrade！

**注意：** npm update --save 在版本 3.11 中似乎有点问题。

​     `npm install taco@latest --save` === `yarn add taco`

​     `npm install taco --global `=== `yarn global add taco` —— 一如既往，请谨慎使用 global 标记。

**二、已知悉的命令**

包和 npm registry 上是一样的。大致而言，Yarn 只是一个新的安装工具，npm 结构和 registry 还是一样的。

​     `npm init `=== `yarn init`

​     `npm link `=== `yarn link`

​     `npm outdated `=== `yarn outdated`

​     `npm publish `=== `yarn publish`

​     `npm run` === `yarn run`

​     `npm cache clean `=== `yarn cache clean`

​     `npm login `=== `yarn login `(logout 同理)

​     `npm test `=== `yarn test`

**三、Yarn 独有的命令**

我跳过了一些提醒我们不要使用的内容，如 `yarn clean`。

​     `yarn licenses ls `—— 允许你检查依赖的许可信息。

​     `yarn licenses generate `—— 自动创建依赖免责声明 license。

​     `yarn why taco` —— 检查为什么会安装 taco，详细列出依赖它的其他包（鸣谢 Olivier Combe）。

​     Emojis

​     速度

​     通过 yarn lockfile 自动实现 shrinkwrap 功能

​     以安全为中心的设计

**四、Npm 独有的命令**

​     `npm xmas `=== NO EQUIVALENT

​     `npm visnup` === NO EQUIVALENT

**总结**

在写这篇文章的时候发现， yarn的run 命令似乎出了点问题，应该会在0.15.2中修复。在这一点上， npm 好多了。以上就是这篇文章的全部内容了，希望本文的内容对大家的学习或者工作能带来一定的帮助，如果有疑问大家可以留言交流。