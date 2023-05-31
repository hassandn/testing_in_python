# testing_in_python
تست هایی که ما خودمون تست میکنیم فیچیر های برنامه اسمشون 
exploratory tests هست

# REPL : read eval print loop
نام دیگر رپل همون پاور شل هست 
نوشته شدن تست در یک فایل مجزا و داشتن یک تابع برای آن را تست کیس میگویند

خب اول خودش اومد یک فایل درست کرد که توش تست مینوشت و اجرا میکرد و در تابع مین مینوشت که اگه همه چی اوکی بود پرینت میکرد اوکی 
ولی حالا فکر کن ما 1000 تا تست داشتیم 
اینطوری خیلی مشکل بود تا بفهمیم مشکل میتونه از چی باشه برای همین تست رانر ها به کار اومدن که برنامه هایی هستن برای تست کردن 
این سه تا از تست رانر ها هستند 
unittest
nose or nose2
pytest

مثلا برای تست کردن تابع sum باید از این تست استفاده کنیم اگه از تست رانر ها استفاده نکنیم 
```python
def test_sum():
    assert sum([1, 2, 3]) == 6, "Should be 6"

def test_sum_tuple():
    assert sum((1, 2, 2)) == 6, "Should be 6"

if __name__ == "__main__":
    test_sum()
    test_sum_tuple()
    print("Everything passed")
```

آگه از unitest استفاده کنیم
یونی تست یک فریمورک و یک تست رانر هست 
برای استفاده کردن از یونی تست باید یک کلاس درست کنی که از unittest.TestCase ارث بری بکنه
```python
import unittest


class TestSum(unittest.TestCase):

    def test_sum(self):
        self.assertEqual(sum([1, 2, 3]), 6, "Should be 6")

    def test_sum_tuple(self):
        self.assertEqual(sum((1, 2, 2)), 6, "Should be 6")

if __name__ == '__main__':
    unittest.main()
```
برای یونی تست ما باید از اول هر تابع تست اندرلاین بنویسیم و بعدش با اسرت ایکوال اونها رو تست میکنیم و در نهایت برای تست کردن تست ها 
از unittest.main() استفاده میکنیم 
جواب به این صورت هست 
```cmd
$ python test_sum_unittest.py
.F
======================================================================
FAIL: test_sum_tuple (__main__.TestSum)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "test_sum_unittest.py", line 9, in test_sum_tuple
    self.assertEqual(sum((1, 2, 2)), 6, "Should be 6")
AssertionError: Should be 6

----------------------------------------------------------------------
Ran 2 tests in 0.001s

FAILED (failures=1)
```
که اینجا یک تست با موفقیت انجام شده و یکیش با شکست مواجه شده 
# nose
وقتی ما صد ها و یا هزاران تست مینویسیم فهمیدن اونها در یونی تست سخت خواهد شد 
برای همین ما میایم و از نوز استفاده میکنیم 
Drop-in replacement 
یعنی اضافه کردن نرم افزار یا سخت افزار بدون تغییر هیچگونه کد و یا پیکر بندی
به خاطر اوپن سورس بودن به مشکل خورده nose و nose2 اگر تازه کار هستید باید استفاده کنید
# pytest
