JavaScript是单线程语言，编程过程中总是要面临大量的异步变成需求，对于初入门的瓜皮来说，总是会面临各种神奇的情景，阅读源码时候也难免遇见各式样的写法和逻辑，以下总结目前已有的几种JavaScript异步编程写法：

	- 回调函数
- 事件监听
- 发布/订阅
- Promise对象
	- async/await



### 一、回调函数

**所谓回调函数，就是把任务的第二段单独写在一个函数里面，等到重新执行这个任务的时候，就直接调用这个函数。**它的英语名字 callback，直译过来就是"重新调用"。

例如Node.js中读取文件

```js
fs.readFile('/etc/passwd', (err,data) = >{
  if(err) throw err;
  console.log(data);
})
```

上面代码中，readFile 函数的第二个参数，就是回调函数，也就是任务的第二段。等到操作系统返回了 /etc/passwd 这个文件以后，回调函数才会执行。

一个有趣的问题是，为什么 Node.js 约定，回调函数的第一个参数，必须是错误对象err（如果没有错误，该参数就是 null）？原因是执行分成两段，在这两段之间抛出的错误，程序无法捕捉，只能当作参数，传入第二段。

### 二、Promise

使用回调函数本身没有问题，但有“回调地狱”的问题。
 假定我们有一个需求，读取完A文件之后读取B文件，再读取C文件，代码如下

```javascript
fs.readFile(fileA,  (err, data) => {
  fs.readFile(fileB,  (err, data) => {
      fs.readFile(fileC, (err,data)=>{
        //do something
    })
  });
});
```

可见，三个回调函数代码看来就够呛了，有时在实际业务中还不止嵌套这几个，难以管理。

这时候**Promise**出现了！它不是新的功能，而是一种新的写法，用来解决“回调地狱”的问题。

我们再假定一个业务，分多个步骤完成，每个步骤都是异步的，而且依赖于上一个步骤的结果，用setTimeout()来模拟异步操作

```javascript
/**
 * 传入参数 n，表示这个函数执行的时间（毫秒）
 * 执行的结果是 n + 200，这个值将用于下一步骤
 */
function A(n) {
    return new Promise(resolve => {
        setTimeout(() => resolve(n + 200), n);
    });
}

function step1(n) {
    console.log(`step1 with ${n}`);
    return A(n);
}

function step2(n) {
    console.log(`step2 with ${n}`);
      return A(n);
}

function step3(n) {
    console.log(`step3 with ${n}`);
     return A(n);
}
```

上面代码中有4个函数，A()返回一个Promise对象，接收参数n，n秒后执行resolve(n+200)。step1、 step2、step3对应三个步骤

现在用Promise实现这三个步骤：

```javascript
function doIt() {
    console.time('do it now')
    const time1 = 300;
    step1(time1)
          .then( time2 =>step2(time2))
          .then( time3 => step3(time3))
          .then( result => {
              console.log(`result is ${result}`)
           });
}

doIt();
```

输出结果如下

```javascript
step1 with 300
step2 with 500
step3 with 700
result is 900
```

result是step3()的参数700+200 = 900。

可见，Promise的写法只是回调函数的改进，用then()方法免去了嵌套，更为直观。
 但这样写绝不是最好的，代码变得十分冗余，一堆的then。
 所以，最优秀的解决方案是什么呢？
 开头暴露了，就是**async/await**
 讲async前我们先讲讲**协程**与**Generator**

### 三、协程

协程(coroutine)，意思是多个线程相互协作，完成异步任务。

它的运行流程如下

- 协程A开始执行
- 协程A执行到一半，暂停执行，执行的权利转交给协程B。
- 一段时间后B交还执行权
- 协程A重得执行权，继续执行

上面的协程A就是一个异步任务，因为在执行过程中执行权被B抢了，被迫分成两步完成。

读取文件的协程代码如下：

```javascript
function task() {
  // 其他代码
   var f = yield readFile('a.txt')
   // 其他代码
}
```

task()函数就是一个协程，函数内部有个新单词**yield**，yield中文意思为退让，
 顾名思义，它表示执行到此处，task协程该交出它的执行权了。也可以把yield命令理解为异步两个阶段的分界线。

协程遇到yield命令就会暂停，把执行权交给其他协程，等到执行权返回继续往后执行。最大的优点就是代码写法和同步操作几乎没有差别，只是多了yield命令。

这也是异步编程追求的，**让它更像同步编程**

### 四、Generator函数

Generator是协程在ES6的实现，最大的特点就是可以交出函数的执行权，懂得退让。

```javascript
function* gen(x) {
    var y = yield x +2;
    return y;
  }
  
  var g = gen(1);
  console.log( g.next()) // { value: 3, done: false }
  console.log( g.next()) // { value: undefined, done: true }
```

上面代码中，函数多了*号，用来表示这是一个Generator函数，和普通函数不一样，不同之处在于执行它不会返回结果，

返回的是指针对象g，这个指针g有个next方法，调用它会执行异步任务的第一步。
 对象中有两个值，value和done，value 属性是 yield 语句后面表达式的值，表示当前阶段的值，done表示是否Generator函数是否执行完毕。

下面看看Generator函数如何执行一个真实的异步任务

```javascript
var fetch = require('node-fetch');

function* gen(){
  var url = 'https://api.github.com/users/github';
  var result = yield fetch(url);
  console.log(result.bio);
}
var g = gen();
var result = g.next();

result.value.then( data => return data.json)
                  .then (data => g.next(data))
```

上面代码中，首先执行Generator函数，得到对象g，调用next方法，此时
 `result ={ value: Promise { <pending> }, done: false }`
 因为fetch返回的是一个Promise对象，（即value是一个Promise对象）所以要用then才能调用下一个next方法。

虽然Generator将异步操作表示得很简洁，但是管理麻烦，何时执行第一阶段，又何时执行第二阶段？

是的，这时候到Async/await出现了！

### 五、Async/await

从回调函数，到Promise对象，再到Generator函数，JavaScript异步编程解决方案历程可谓辛酸，终于到了Async/await。很多人认为它是异步操作的最终解决方案(谢天谢地，这下不用再学新的解决方案了吧)

其实async函数就是Generator函数的语法糖，例如下面两个代码：

```javascript
var gen = function* (){
  var f1 = yield readFile('./a.txt');
  var f2 = yield readFile('./b.txt');
  console.log(f1.toString());
  console.log(f2.toString());
};
var asyncReadFile = async function (){
  var f1 = await  readFile('./a.txt');
  var f2 = await  readFile('./b.txt');
  console.log(f1.toString());
  console.log(f2.toString());
};
```

上面的为Generator函数读取两个文件，下面为async/await读取，比较可发现，两个函数其实是一样的，async不过是把Generator函数的*号换成async，yield换成await。

#### 1.async函数用法

上面说了async不过是Generator函数的语法糖，那为什么要取这个名字呢？自然是有理由的。
 async是“异步”，而await是async wait的简写，即异步等待。所以应该很好理解async用于声明一个function是异步的，await用于等待一个异步方法执行完成

下面来看一个例子理解async命令的作用

```javascript
async function test() {
  return "async 有什么用？";
}
const result = test();
console.log(result) 
```

输出：
 `Promise { 'async 有什么用？' }`
 可以看到，输出的是一个Promise对象！
 所以，async函数返回的是一个Promise对象，如果直接return 一个直接量，async会把这个直接量通过PromIse.resolve()封装成Promise对象

**注意点**
 一般来说，都认为await是在等待一个async函数完成，确切的说等待的是一个表示式，这个表达式的计算结果是Promise对象或者是其他值（没有限定是什么）

即await后面不仅可以接Promise，还可以接普通函数或者直接量。

同时，我们可以把async理解为一个运算符，用于组成表达式，表达式的结果取决于它等到的东西

- 等到非Promise对象 表达式结果为它等到的东西
- 等到Promise对象  await就会阻塞后面的代码，等待Promise对象resolve，取得resolve的值，作为表达式的结果

还是那个业务，分多个步骤完成，每个步骤依赖于上一个步骤的结果，用setTimeout模拟异步操作。

```javascript
/**
 * 传入参数 n，表示这个函数执行的时间（毫秒）
 * 执行的结果是 n + 200，这个值将用于下一步骤
 */
function takeLongTime(n) {
    return new Promise(resolve => {
        setTimeout(() => resolve(n + 200), n);
    });
}

function step1(n) {
    console.log(`step1 with ${n}`);
    return takeLongTime(n);
}

function step2(n) {
    console.log(`step2 with ${n}`);
    return takeLongTime(n);
}

function step3(n) {
    console.log(`step3 with ${n}`);
    return takeLongTime(n);
}
```

async实现方法

```javascript
async function doIt() {
    console.time("doIt");
    const time1 = 300;
    const time2 = await step1(time1);
    const time3 = await step2(time2);
    const result = await step3(time3);
    console.log(`result is ${result}`);
    console.timeEnd("doIt");
}

doIt();
```

输出结果和上面用Promise实现是一样的，但这个代码结构看起来清晰得多，几乎跟同步写法一样。

#### 2. async函数的优点

（1）**内置执行器**
 Generator 函数的执行必须靠执行器，所以才有了 co 函数库，而 async 函数自带执行器。也就是说，async 函数的执行，与普通函数一模一样，只要一行。

（2） **语义化更好**
 async 和 await，比起星号和 yield，语义更清楚了。async 是“异步”的简写，而 await 可以认为是 async wait 的简写。所以应该很好理解 async 用于申明一个 function 是异步的，而 await 用于等待一个异步方法执行完成。

（3）**更广的适用性**
 yield 命令后面只能是 Thunk 函数或 Promise 对象，而 async 函数的 await 命令后面，可以跟 Promise 对象和原始类型的值（数值、字符串和布尔值，但这时等同于同步操作）。