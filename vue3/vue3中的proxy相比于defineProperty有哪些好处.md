

vue2 用的是object.defineproperty ,但该api 对数组拦截又问题，vue2 需要专门为数组响应又实现了一遍。而且不能拦截那些新增的删除的属性。另外 object.defineproperty 在初始化时候需要深度递归待处理的对象才能对它进行完全的拦截，明显的增加了初始化的时间。

而proxy可以直接对数组进行拦截，可以监听的到增删，还能对Map 和 Set 实现拦截，另外Proxy 的拦截也是懒处理行为，如果用户没有访问嵌套对象，那么也不会实施拦截，这就让初始化的速度和内存的占用都改善了。