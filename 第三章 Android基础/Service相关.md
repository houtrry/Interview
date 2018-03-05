## service的应用场景,以及和Thread区别
1. Service是一种可以在后台执行长时间运行操作而没有界面的应用组件.Service运行在主线程中. 不能在Service中直接做耗时操作(做耗时操作只能在Thread中).

## 开启Service的两种方式以及区别
### 1. startService
1. 定义一个类集成Service
2. 在Manifest.xml文件中配置该Service
3. 使用Context的startService(intent)方法启动该Service
4. 不再使用时,调用stopService(intent)方法停止该服务

### 2. bindService
1. 创建BindService服务端,继承自Service并在勒种创建一个实现了IBinder接口的实例对像并提供公共方法给客户端调用
2. 从onBind()回调方法返回此Binder实例
3. 在客户端中,从onServiceConnected()回调方法接收Binder,并使用提供的方法调用绑定服务