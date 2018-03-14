## 什么是AsyncTask
本质上就是一个封装了线程池和Handler的异步框架，主要用来执行异步任务。

### 三个参数
1. 
### 五个方法
1. onPreExcute:耗时操作还没执行前，做一些初始化操作。运行在UI线程。
2. doInBackground：做耗时操作。执行在onPreExcute后面，运行在工作线程。该方法的返回值作为onPostExecute的参数。该方法中可以调用publishProgress方法，最终会传给onProgressUpdate方法，一般用来更新进度。
3. publishProgress：与onProgressUpdate配合使用，用来更新进度。
4. onProgressUpdate:UI线程。在工作线程中调用publishProgress，最终会调用onProgressUpdate方法，publishProgress的参数作为onProgressUpdate的参数。
5. onPostExecute：UI线程。工作结束后调用。

### AsyncTask的机制原理
1. AsyncTask的本质上是一个静态的线程池，AsyncTask派生出的子类可以实现不同的异步任务，这些任务都是提交到静态的线程池中执行。
2. 线程池中的工作线程执行doInBackground(mParams)方法执行异步任务。
3. 当任务状态改变后，工作线程会向UI线程发送消息，AsyncTask内部的IntentHandler会响应这些消息，并调用相关的回调函数。


### AsyncTask的注意事项
1. 内存泄露： 非静态内部类持有外部类的引用，解决方法与Handler类似
2. 生命周期： 生命周期结束的时候，工作线程没结束的情况。在onDestroy中调用AsyncTask的cancel方法。
3. 结果丢失： 与上面的原因一样
4. 并行or串行： 建议使用串行