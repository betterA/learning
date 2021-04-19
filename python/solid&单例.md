# solid 设计原则

1. **单一责任原则**
2. **开发封闭原则**   【对扩展开放，对修改封闭】 
3. **里氏替换原则**     
4. 依赖倒置原则       
5. 接口分离原则 

# 单例模式

1. 对象只存在一个实例

2. `__init__`和`__new__`的区别：

      `__new__`是实例创建之前被调用，返回改该实例对象，是静态方法
   
      `__init__`是实例对象创建完成后被调用，是实例方法
      `__new__`先被调用，`__init__`后被调用
      `__new__`的返回值（实例）将传递给`__init__`方法的第一个参数，`__init__`给这个实例设置相应参数



```python
# 1 from xx import xxx 是最简单的单例模式 (线程安全的) import是线程安全

# 2 装饰器
def singleton(cls):
    instances = {}
    def getinstance():
        if cls not in instances:
            instances[cls] = cls()
        return instances[cls]
    return getinstance

@singleton
class MyClass:
    pass

# 3 __new__ 方式实现单例   
class Singleton2(object):
    __isinstance = False
    def __new__(cls, *args, **kwargs):
        if cls.__isinstance:
            return cls.__isinstance
        cls.__isinstance = object.__new__(cls)
        return cls.__isinstance
    
# 多线程需要加锁
import threading
class SingletonByThread(object):
    objs = {}
    objs_locker = threading.Lock()
    def __new__(cls, *args, **kwargs):
        if cls in cls.objs:
            return cls.objs[cls]
        cls.objs_locker.acquire()
        try:
            if cls in cls.objs: # 两次检查[double check]
                return cls.objs[cls]
            cls.objs[cls] = object.__new__(cls)
        finally:
            cls.objs_locker.release()
```

