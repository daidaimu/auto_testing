### python类方法

- 实例化   静态方法   类方法

  ```python
  class student:
    	
      age = 18
      def __init__(self, name):
          self.name = name
  
      def std_name(self):        # self表示的是实例本身,可以访问自己的属性，调用自己方法
          print(self.name)
  
      @staticmethod
      def std_name1():           # 对传参数没有要求，类可以直接调用   studen.std_name1()
          print("hahaha")
       
  
      @classmethod
      def std_name3(cls):				# 必须带cls, cls表示student这个类，支持实例调用和类直接访问
          print(cls.name)
         
  ```

- 调用方法

  ```
  先实例化： A= student("Tony")
  可调用方法： A.std_name(), 
  ```

  

