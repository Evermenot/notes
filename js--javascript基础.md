## JavaScript

#### 一.数组方法

```javascript
/* sort()方法

1. 定义：对数组的元素进行排序
2. 语法：arrayObject.sort(sortby)     参数可选,且必须为函数

3. 实例：
     实例1：不传参情况，该方法默认将数组元素转换成字符串，按照字符编码顺序进行排序
     实例2：传入参数
            var arr = new Array(5,2,4,1,3);
            function sortbyArgs(a, b) {
              return a - b;
            }
            var result = arr.sort(sortbyArgs);
            console.log(result)    // 结果： 1 2 3 4 5  (默认从小到大排序)
            
      注：如果将返回值改为 b - a  将按照从大到小排序  (结合下面可理解原因)
      
4. 原理: 参数 a 和 b 在调用时相当于取出数组的前两个值, sort方法根据传入的参数函数返回值的          
         正负或者0,来判断如何排序类似于冒泡排序.
         默认a - b < 0 时,a和b不交换位置(即a还在b前);
         a - b > 0 时,a和b交换位置(a换到b后);
```

