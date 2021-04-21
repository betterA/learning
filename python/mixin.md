```python
class Displayer():
    def display(self, message):
        print(message)


class LoggerMixin():
    def log(self, message, filename='logfile.txt'):
        with open(filename, 'a') as fh:
            fh.write(message)


    def display(self, message):
        super(LoggerMixin, self).display(message)  # 在subclass实例执行这个方法
        self.log(message)


class MySubClass(LoggerMixin, Displayer):
    def log(self, message):
        super().log(message, filename="subclasslog.txt")


sb = MySubClass()
sb.display("wahaha")
print(MySubClass.mro())
"""
wahaha
[<class '__main__.MySubClass'>, <class '__main__.LoggerMixin'>, <class '__main__.Displayer'>, <class 'object'>]
"""
```