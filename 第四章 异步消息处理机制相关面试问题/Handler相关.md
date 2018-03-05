## Handler相关问题
1. Handler的作用：用于线程间通信。
2. 一个线程可以有多个Handler，但是至多只能有一个Looper和MessageQueue。如果一个线程中已经存在Looper，再次调用Looper.prepare()创建Looper会抛出异常。

```

    public static void prepare() {
        prepare(true);
    }

    private static void prepare(boolean quitAllowed) {
        if (sThreadLocal.get() != null) {
            throw new RuntimeException("Only one Looper may be created per thread");
        }
        sThreadLocal.set(new Looper(quitAllowed));
    }
```

## Handler的内存泄露
1. 内存泄露的原因： 非静态内部类对象持有外部类的的引用，导致外部activity无法释放。
2. 解决办法：handler内部类持有外部类的弱引用，并把handler改为静态内部类，Activity#onDestroy的时候调用mHandler.removeCallback()