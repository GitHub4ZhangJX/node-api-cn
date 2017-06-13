<!-- YAML
added: v6.1.0
-->

* `previousValue` {Object} A previous return value from calling
  `process.cpuUsage()`
* Returns: {Object}
    * `user` {integer}
    * `system` {integer}

process.cpuUsage（）方法返回当前进程的用户和系统CPU时间使用情况，该对象具有属性user和system，其值为微秒值（百万分之一秒）。这些值分别测量在用户和系统代码中花费的时间，如果多个CPU内核正在执行此过程，则可能会最终超过实际耗用的时间。

以前调用process.cpuUsage（）的结果可以作为参数传递给函数，以获取diff读取。

```js
const startUsage = process.cpuUsage();
// { user: 38579, system: 6986 }

// spin the CPU for 500 milliseconds
const now = Date.now();
while (Date.now() - now < 500);

console.log(process.cpuUsage(startUsage));
// { user: 514883, system: 11226 }
```

