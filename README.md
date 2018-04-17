### 100 种 数组去重的方法
```s
    1. 定义一个新数组，并存放原数组的第一个元素，然后将元素组一一和新数组的元素对比，若不同则存放在新数组中。
    2. 先将原数组排序，在与相邻的进行比较，如果不同则存入新数组。
    3. 利用对象属性存在的特性，如果没有该属性则存入新数组。
    4. 利用数组的indexOf下标属性来查询。
    5. 利用数组原型对象上的 includes 方法
    6. 利用数组原型对象上的 filter 和 includes方法。
    7. 利用数组原型对象上的 forEach 和 includes 方法。
    8. 利用数组原型对象上的 splice 方法。
    9. 利用数组原型对象上的 lastIndexOf 方法。
    10.利用 ES6的 Array.from 和 set 方法。
    11.利用es6 的 set 方法 和可扩展运算符

```






```html

<body>
    <h1>数组去重 - 1 </h1>
    <h2>定义一个新数组，并存放原数组的第一个元素，然后将元素组一一和新数组的元素对比，若不同则存放在新数组中。</h2>
    <script>
        function unique(arr) {
            var res = [arr[0]];

            for (var i = 1; i < arr.length; i++) {
                repeat = false;
                for(var j = 0; j < res.length; j ++){
                    if (arr[i] === res[j]) {
                        repeat = true;
                        break;
                    }
                }
                if (!repeat) {
                    res.push(arr[i]);
                }
                
            }
            return res;
        }
        console.log('------------方法一---------------');

        console.log(unique([1, 1, 2, 3, 5, 3, 1, 5, 6, 7, 4]));
    </script>
</body>
```

```html

<body>
    <h1>数组 去重 - 2 </h1>
    <h2> 思路：先将原数组排序，在与相邻的进行比较，如果不同则存入新数组。</h2>
    <script>
        function unique2(arr) {
            var arr2 = arr.sort();
            // arr2 = [1, 2, 3 ,5 ,... ]
            var res = [arr2[0]];
            for (var i = 1; i < arr2.length; i++) {
                // arr2[i]  === [1, 1, 2, 3, 5, ...]
                // res[res.length - 1] === [1, 2, 3 ...]

                if (arr2[i] !== res[res.length - 1]) {
                    res.push(arr2[i]);
                }
            }
            return res;
        }

        console.log('------------方法二---------------');

        console.log(unique2([1, 1, 2, 3, 5, 3, 1, 5, 6, 7, 4, 'a', 'b', 'a']));
    </script>
</body>
```

```html

<body>
    <h1>数组去重 - 3</h1>
    <h2>利用对象属性存在的特性，如果没有该属性则存入新数组。</h2>
    <script>
        function unique3(arr) {
            var res = [];
            var obj = {};
            for (var i = 0; i < arr.length; i++) {
                if (!obj[arr[i]]) {
                    obj[arr[i]] = 1;
                    res.push(arr[i]);
                }
            }
            // console.log(obj)
            obj = null 
            return res;
        }

        console.log('------------方法三---------------');

        console.log(unique3([1, 1, 2, 3, 5, 3, 1, 5, 6, 7, 4]));
    </script>
</body>

```

```html
<body>
    <h1>数组去重 - 4</h1>
    <h2>利用数组的indexOf下标属性来查询。</h2>
    <script>
        function unique4(arr) {
            var res = [];
            for (var i = 0; i < arr.length; i++) {
                if (res.indexOf(arr[i]) == -1) {
                    res.push(arr[i]);
                }
            }
            return res;
        }

        console.log('------------方法四---------------');

        console.log(unique4([1, 1, 2, 3, 5, 3, 1, 5, 6, 7, 4]));
    </script>
</body>
```

```html
<body>
    <h1>数组去重 5 </h1>
    <h2>利用数组原型对象上的 includes 方法</h2>
    <script>
        function unique5(arr) { 
            var res = [];   
            for (var i = 0; i < arr.length; i++) {  
                if (!res.includes(arr[i])) { // 如果res新数组包含当前循环item
                       
                    res.push(arr[i]);  
                } 
            } 
            return res;
        } 
        console.log('------------方法五---------------'); 
        console.log(unique5([1, 1, 2, 3, 5, 3, 1, 5, 6, 7, 4]));
    </script>
</body>
```

```html
<body>
    <h1>数组去重 - 6</h1>
    <h2>利用数组原型对象上的 filter 和 includes方法。</h2>
    <script>
        function unique6(arr) {
            var res = [];

            res = arr.filter(function (item) {
                return res.includes(item) ? '' : res.push(item);
            });
            return res;
        }

        console.log('------------方法六---------------');

        console.log(unique6([1, 1, 2, 3, 5, 3, 1, 5, 6, 7, 4]));
    </script>
</body>
```

```html
<body>
    <h1>数组去重 - 7</h1>
    <h2>利用数组原型对象上的 forEach 和 includes 方法。</h2>
    <script>
        function unique7(arr) {
            var res = [];

            arr.forEach(function (item) {
                res.includes(item) ? '' : res.push(item);
            });
            return res;
        }

        console.log('------------方法七---------------');

        console.log(unique7([1, 1, 2, 3, 5, 3, 1, 5, 6, 7, 4]));
    </script>
</body>
```

```html
<body>
    <h1>数组去重 - 8</h1>
    <h2>利用数组原型对象上的 splice 方法。</h2>
    <script>
        function unique8(arr) {
            var i,j,len = arr.length;
            for (i = 0; i < len; i++) {
                for (j = i + 1; j < len; j++) {
                    if (arr[i] == arr[j]) {
                        arr.splice(j, 1);
                        len--;
                        j--;
                    }
                }
            }
            return arr;
        }

        console.log('------------方法八---------------');

        console.log(unique8([1, 1, 2, 3, 5, 3, 1, 5, 6, 7, 4]));
    </script>
</body>
```
```html

<body>
    <h1>数组去重 - 9</h1>
    <h2>利用数组原型对象上的 lastIndexOf 方法。</h2>
    <script>
        function unique9(arr) {
            var res = [];
            for (var i = 0; i < arr.length; i++) {
                res.lastIndexOf(arr[i]) !== -1 ? '' : res.push(arr[i]);
            }
            return res;
        }

        console.log('------------方法九---------------');

        console.log(unique9([1, 1, 2, 3, 5, 3, 1, 5, 6, 7, 4]));
    </script>
</body>
```
```html
<body>
    <h1>数组去重 - 10</h1>
    <h2> 利用 ES6的 Array.from 和 set 方法。</h2>
    <script>
        // function unique10(arr) {
        //     // Set数据结构，它类似于数组，其成员的值都是唯一的
        //     return Array.from(new Set(arr)); // 利用Array.from将Set结构转换成数组
        // }

        // console.log('------------方法十---------------');

        // console.log(unique10([1, 1, 2, 3, 5, 3, 1, 5, 6, 7, 4]));



       
    </script>
</body>
```
```html

<body>
    <h1>数组去重 - 11</h1>
    <h2>利用es6 的 set 方法 和可扩展运算符</h2>
    <script>
        const arr = [1, 1, 3, 3, 3, 2, 5, 5]

        console.log([...new Set(arr)]);

        console.log([...new Set(arr)] instanceof Array);
        
        
        // 此方法 检查 是否是数组
        console.log(Object.prototype.toString.call(arr) === '[object Array]'); // true
    </script>
</body>
```

[转载  十种数组去重](http://www.jb51.net/article/121410.htm)

[ 原生如何检测变量是否是一个数组的几种方法](https://blog.csdn.net/oliverpeng1521314/article/details/70980129)