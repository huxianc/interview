- 宏任务：script/setTimeout/setInterval/setImmediate/ I/O / UI Rendering
- 微任务：process.nextTick()/Promise

script 标签是宏任务，先执行这个宏任务，然后里面的代码是先微任务，在宏任务，如果宏任务里面又有宏、微任务，按着微任务->宏任务的执行顺序进行

### 参考链接

- https://zhuanlan.zhihu.com/p/257069622
