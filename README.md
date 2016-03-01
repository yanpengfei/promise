promise的实现，先以html方式上传，方便调试。


promise的基本原理，是
1. 通过数组维护then方法传入的函数队列，then方法就是把then的参数压入一个队列。
2. promise执行的时候传入的函数，实际是将promise对象内部的resolve和reject暴露出来给这个函数内部调用。
3. resolve和reject通过next方法,通过setTimeout(fn,0)的小技巧将then函数的地址根据then的顺序依次压入事件队列，当第一个resolve启动的时候，就会顺序执行了。

