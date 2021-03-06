# 数组
 * `Array` 是一个函数 返回一个数组
 * `Array(x,y,z)` 将参数变成一个数组返回`[x,y,z]`
 * 只有一个`参数`，并且参数是`数字n`，返回长度位`n`的空数组
## 类扩展方法
### Array.of( )
* 参数为`一个数字`的时候返回为只有`一个数字的数组`
### Array.from( )
* Array.from(`数组/类数组`)，返回`数组`
```js
let a = Array.from([1,2,3.4]) // a = [1,2,3,4]
let b = Array.from("123") // b = [1,2,3]
```
* 可以接收第二个参数，作用类似于map方法，用来对每个元素进行处理，将处理过的值放回到返回的数组
```js
Array.from(arrayLike, x => x * 2)
```
* ES5中的替代方案
> let arr = [ ].slice.call(`类数组`)

* 类数组对象 => 必须有`length`属性
```js
Array.from({length:3}) // [undefined,undefined,undefined]
```

## 原型链上的方法
### 一般方法
#### copyWithin
* 从原数组中读取内容 替换数组中`指定位置`的内容
* copyWithin(\[target]，\[start(默认为0)], \[end(不包括，不写默认到结束)])
* 会改变原数组，但是长度不变
```js
let arr = [1,2,3,4,5,6,7,8]
let res = arr.copyWithin(4,2,4)  // res = [1,2,3,4,3,4,7,8]
```
#### fill
* fill(\['指定元素'],\[开始位置],\[结束位置])
* 将数组的每一项变成指定字符
#### includes
* 查找数组中有没有某一项，返回`布尔值`
* include(\[指定元素]，\[开始位置])
* 可以规避indexOf对NaN的错误判断
#### in
* 判断数组`索引`上是否有值，返回`布尔值`
```js
let arr = [,,,,,]  // 有几个逗号数组长度就是几
let arr2 = [,,,,undefined] //undefined 不是空位
```
* `在es5中直接跳过空位`，`在es6中将空位处理成undefined`

### 可遍历方法
> 除了`reduce`&`reduceRight`方法,其余方法的第一个参数是一个函数，这个函数中的this指向window，
可以通过第二参数的来改变第一个函数中this的指向
#### filter
* 遍历数组，返回`true`的元素被保留
```js
filter(function ([item],[index],[原数组]){ return })
```
#### find
* 遍历数组，一旦返回`true`，停止查找，返回`当前项`
```js
// 模拟源码
Array.prototype.myFind = conditionFunc => {
  for (let i = 0; i < this.length; i++){
    if  (conditionFunc(this[i],i)){
      return this[i]
    }
  } 
}
```
#### findIndex
* 遍历数组，一旦返回`true`，停止查找，返回`当前项的索引`
#### every
* 遍历数组，一旦返回`false`，停止遍历，返回`false`
#### some
* 遍历数组，一旦返回`true`，停止遍历，返回`true`
#### reduce
* 迭代
* reduce(function (\[prev]，\[item]){},\[初始值])
```js
let arr = [1,2,3,4]
arr.reduce(function (pre,item){
    // pre 上一次的返回值
    //item 当前项
    return pre+item
})
```
#### reduceRight
* 和reduce一样只不过是从右边开始
#### keys
* 遍历每一项 `索引` 的接口 使用for of 遍历
```js
let arr = [1,2,3,4]
for(let key of arr.keys()){
    console.log(key) // 0,1,2,3
}
for(let key of arr){
    console.log(key) //1,2,3,4
}
```
#### entries
* 遍历接口 可以遍历到索引和数组的每一项,每一次遍历得到一个数组`\[索引，当前项]`
```js
let arr = [1,2,3,4]
for(let a of arr){
    console.log(a); // [0,1],[1,2],[2,3],[3,4]
}
for(let [index,item] of arr){
    console.log(index,item); //
}
```




