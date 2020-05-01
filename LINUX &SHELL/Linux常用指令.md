### vim



### read

alias: 函数别名   alias ssh='tanwenjian'



```python
import unittest
from HTMLTestRunner import HTMLTestRunner
import time



testcase_dir = "./"
test_report = "./report"
discover = unittest.defaultTestLoader.discover(testcase_dir, pattern="test*.py")

if __name__ == "__main__":
    now = time.strftime("%Y-%m-%d %H:%M:%S")
    filename = test_report + "/" + now + 'result.html'
    fp = open(filename, 'wb')

    runner = HTMLTestRunner(stream=fp, title="测试用例执行", description="处女作")
    runner.run(discover)
    fp.close()

```



