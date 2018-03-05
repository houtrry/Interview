##  Fragment加载到Activity的两种方式
1. 添加Fragment到Activity的布局文件当中.通过FragmentMagager与FragmentTransaction在Java代码中添加
2. 动态在activity中添加fragment

## FragmentPagerAdapter与FragmentStatePagerAdapter的区别
1. FragmentPagerAdapter适用于页面较少的情况.FragmentStatePagerAdapter适用于页面较多的情况.
2. FragmentStatePagerAdapter在每次ViewPager切换item的时候,会回收内存(回收之前的item).FragmentPagerAdapter没有回收内存,只是分离了UI

## Fragment的生命周期


## Fragment通信
1. 在Fragment中调用Activity中的方法->getActivity
2. 在Activity中调用Fragment中的方法->接口回调(Fragment中定义接口,Activity来实现接口)
3. 在Fragment中调用Fragment中的方法->findFragmentById

## Fragment中的replace/add/remove方法
