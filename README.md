# Promise的实现

### Promise的应用场景
###### 个人认为主要解决多个异步互相依赖场景的组织

### Promise对象的状态
###### 通过Promise类实例话的对象有三种状态，分别是：Fulfilled，Rejected，Pending

### Promise对象的方法
###### 1. Promise对象：通过实例化Promise类来产生Promise对象，对象具有then,catch,all方法。
###### 2. then方法：参数：函数；表示resolve执行后的下一个执行方法
###### 3. catch方法：参数:函数；表示reject执行后执行的方法
###### 4. all方法：参数：Promise对象数组；表示数组内所有的Promise对象状态都确定之后才会调用then方法
###### 5. Promise.resolve：new Promise的快捷方式
###### 6. Promise.reject:  new Promise的快捷方式

### Promise的基本原理
###### 1. 通过数组维护then方法传入的函数队列，then方法就是把then的参数压入一个队列。
###### 2. Promise执行的时候传入的函数，实际是将Promise对象内部的resolve和reject暴露出来给这个函数内部调用。
###### 3. resolve和reject通过next方法,依次压入事件队列，当第一个resolve启动的时候，调度代码(setTimeout(fn,0)内的代码)就会顺序执行了。
###### 4. 所有的then方法都放在数组内，通过栈的方式维护，调度代码会放到事件队列内，进行栈的操作。
