### HandlerThread 的特点
* HandlerThread 本质上是一个线程类，它继承了Thread
* HandlerThread有自己内部的Looper对象，可以进行looper循环。
* 通过获取HanndlerThread的looper对象传递给Handler对象，可以在handleMessage方法中执行异步任务
* 优点是不会有堵塞，减少了对性能的消耗，缺点是不能同时进行多任务的处理，需要等待进行处理，效率比较低。
* 与线程池注重并发不同，HandlerThread是一个串行队列，HandlerThread背后只有个一个线程。