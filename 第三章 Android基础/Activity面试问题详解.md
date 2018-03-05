## Activity的四种状态
1. running: Activity处于栈顶，可以与用户交互。
2. paused: 失去焦点时（被一个非全屏的Activity遮挡或者透明半透明的Activity遮挡）的时候，Activity无法交互，但没被销毁.内存不紧张，则不会回收
3. stopped: 被另外一个Activity完全覆盖够，处于此状态。内存不紧张，则不会回收
4. killed:被回收
## Activity的生命周期
1. onCreate() => onStart()=> onResume() => running => onPause() => onStop() => onDestroy()
2. onStart/onStop: Activity是否可见
3. onResume/onPause:Activity是否有焦点（有焦点才能响应用户交互）
4. 点击Home键回到主界面：onPause() => onStop()   再次回到原Activity： onRestart()=>onStart()=>onResume()
## Activity的进程优先级
前台、可见、服务、后台、空

## Activity的启动模式
1. standard: 每次启动一个Activity都会创建新的，不会复用。
2. singleTop: 栈顶复用模式。栈顶有则复用。
3. singleTask: 栈内复用模式。栈内有则复用。栈内有则清除该Activity上面所有的Activity，使该Activity位于栈顶。
4. singleInstance：独享一个栈

## scheme跳转协议
1. [scheme简单介绍](http://blog.csdn.net/lishuiyuntian/article/details/77477756)
2. [scheme的安全问题](https://segmentfault.com/a/1190000007747812).
