## 220917

<img src='./img/2022-09-17-14-50-25.png' height=333px></img>  
课程内容

<img src='./img/2022-09-17-14-51-41.png' height=333px></img>  
引入原因  
区块链计算储存资源昂贵，所以分链上和链下逻辑  
以太坊中用 offchain daemon 监听以太坊传出的事件，获取信息并计算，有必要的话，将结果通过 rpc transaction 形式返回链上存储。  
substrate 类似，但在 offchain 做了创新 ooov 0240。

<img src='./img/2022-09-17-16-25-49.png' height=333px></img>  
substrate 把 offchain 逻辑搬到了 runtime 里。  
让链下逻辑共享链上逻辑的升级方式 dddf。

<img src='./img/2022-09-17-16-28-02.png' height=333px></img>  
总结 substrate offchain worker 的优势

<img src='./img/2022-09-17-16-28-59.png' height=333px></img>  
三大组件  
具体内容在链接里查看。

<img src='./img/2022-09-17-16-29-34.png' height=333px></img>  
官方文档介绍

<img src='./img/2022-09-17-16-30-22.png' height=333px></img>  
上面所说的三大组件完成后，形成这样的一套模式 dddf ooov

<img src='./img/2022-09-17-16-32-42.png' height=333px></img>  
offchain 架构补充说明  
就是各种读写权限

<img src='./img/2022-09-17-16-39-28.png' height=333px></img>  
官网提取的，offchain worker 功能  
1，朝链上提交交易  
2，实现了一个完整的 http 客户端，可以做 http/https 请求  
3，访问本地 local keystore，也就是账户信息，才能对交易进行签名和验证  
5，随机数产生器，因为是链下，可以用本机的真随机数  
6，访问本地的精确时间  
7，sleep and resume work  
所有这些功能会在本课的 8 个实例中有展示。

<img src='./img/2022-09-17-16-45-42.png' height=333px></img>  
如何实现一个 offchain worker

<img src='./img/2022-09-17-16-47-59.png' height=333px></img>  
--=  
<img src='./img/2022-09-17-16-47-31.png' height=333px></img>  
仅仅是在 pallets/template 里添加了这段就实现了一个 ofc worker。  
这里使用的是 0.9.28 tag。  
add220918  
<img src='./img/2022-09-28-09-41-46.png' height=333px></img>  
除此之外，toml 里还要添加 log 依赖

<img src='./img/2022-09-17-16-51-16.png' height=333px></img>  
build 并 dev 启动后，看到了效果  
每次 ofc 都是在 imported 后执行的，也就是块倒入后执行  
每导入一个块，执行一次。

<img src='./img/2022-09-17-17-09-50.png' height=333px></img>  
--=  
<img src='./img/2022-09-17-17-11-11.png' height=333px></img>  
--=  
<img src='./img/2022-09-17-17-13-34.png' height=333px></img>  
示例 2  
这几个 hook 函数的函数签名，也就是传参的类型，格式，返回的类型都是一致的，substrate 框架定义好的。照着写就行。  
因为是在 dev 模式，又是出块节点，又是共识节点 dddf。  
注意三个是导入块之前执行，一个是导入后执行。

<img src='./img/2022-09-17-17-18-28.png' height=333px></img>  
--=  
<img src='./img/2022-09-17-17-20-15.png' height=333px></img>  
示例 3  
有可能逻辑会超过出块时间 6 秒  
2550 ooov  
此段代码是大概执行一个 ofc，持续 8 秒才结束。

<img src='./img/2022-09-17-17-23-52.png' height=333px></img>  
ofc 编程模式  
定时器流模式，定时重入  
默认 6 秒，在 6 秒后出块，就执行一下函数  
与响应式不同，响应式应该就是平常的那种模式
