# Utils
导入
````js
  import { Utils } form 'dt-utils';
````
## isMacOs
判断设备是否是Mac
```js
  Utils.isMacOs(); //boolean
```
## isWindows
判断设备是否是Windows
```js
  Utils.isWindows(); //boolean
```
## isMobileDevice
判断设备是否是移动设备
```js
  Utils.isMobileDevice(); //boolean
```
## browserCheck
浏览器类型和版本检测

`true`表示通过兼容性检测,`false`表示不通过兼容性检测

```js
  Utils.browserCheck(); //boolean 
```
## checkExist
检查属性是否存在
```js
  Utils.checkExist()
```
例如:
```js
  Utils.checkExist('') // false
  Utils.checkExist(null) // false
  Utils.checkExist(undefined) // false
```
## getParameterByName
根据参数名获取URL数据

```js
 /**
   * 获取图片的Base64格式
   *  @param  {[type]} name [description]
   * @param  {[type]} url  [description] 可选参数，默认当前域
   */
  Utils.getParameterByName(); //boolean 
```

例如:
```js
  Utils.getParameterByName('name','http://baidu.com?name='1'); // 1 
  Utils.getParameterByName('name'); // 1 
```
## getBase64
获取图片的Base64格式

```js
  /**
   * 获取图片的Base64格式
   * @param  {[type]}   img      [description]
   * @param  {Function} callback [description]
   */
  Utils.getBase64(img,callback); 
```
## percent
百分比转换

````js
   /**
   * @param  {[type]} num       [description]
   * @param  {[type]} precision [description]
   */
  Utils.percent(num: number, precision?: number); 
````
例如:

````js
 Utils.percent(1); // 100%
 Utils.percent(0.5); // 50%
 Utils.percent(0.54); // 54%
 Utils.percent(0.54321); // 54.32%
 Utils.percent(0.54321,1); // 54.3%
 Utils.percent(0.54321,2); // 54.32%
 Utils.percent(0.54321,3); // 54.321%
````
## getCssText
  样式对象转css style风格转字符串

````js
/**
 * @param {Record<string, any>} [object={}]
 * @returns String
 */
  Utils.getCssText(object: Record<string, any> = {}); 
````
例如:

````js
  let styles = {
    height:'100px',
    width:'100px',
    color:'red'
  }
  Utils.getCssText(styles); // 'height:100px;width:100px;color:red;'
````

## trim
去除头尾空格
```js
    /**
    * @returns string
    */
    trimlr (str: string)
```
例如:
```js
trim(' 12 3 1    23  ') // "12 3 1    23"
```

## removeAllSpaces
去除字符串全部空串
```js
    /**
    * @returns string
    */
    removeAllSpaces (str: string)
```
例如:
```js
removeAllSpaces(' aa bb ') // "aabb"
```
## convertBytes
转换 Byte 转换为小于1024值最大单位
```js
convertBytes (value: number): string
```
例如:
```js
convertBytes(102) // 102 B
convertBytes(1024) // 1 KB
convertBytes(1024*1024) // 1 MB
```
## toQfw
千位分割
```js
toQfw (str: string): string
```
例如:
```js
toQfw('123123') // "123,123"
```

## textOverflowExchange
文字溢出转换
```js
textOverflowExchange (str: string, num: number): string
```
例如:
```js
textOverflowExchange('my name is sichen', 10) // "my name is..."
```

## jsonFormat
json格式化

```js
// 格式化内容: text
// 格式化占位符: space
jsonFormat (text: string, space?: number)
```

## sortByCompareFunctions
多函数排序，匹配到0为止
```js
sortByCompareFunctions (arr: any[], ...compareFunctions: any[])
```

## exchangeOrder
转换排序字段
```js
exchangeOrder (order: string): string {
    switch (order) {
        case 'ascend':
            return 'asc';
        case 'descend':
            return 'desc';
        default:
            return undefined;
    }
}
```
例如:
```js
exchangeOrder('ascend') // 'asc'
exchangeOrder('descend') // 'desc'
exchangeOrder('abc') // undefined
```


## generateAKey
生成一个随机key

例如:
```js
generateAKey(): string // "1594806665598655835"
```

## isJSONStr
判断是否是JSON string
```js
isJSONStr (str: string): boolean
```
例如:
```js
isJSONStr('name') // false
```


## getRandomStr
随机生成一串len位同时包含数字、大小写字母的字符串
```js
    getRandomStr (len: number): string
```
例如:
```js
getRandomStr(10) // "5vK6vT6sL8"
```

## isEqualArr
简单地判断数组是否相等
```js
isEqualArr (arr1: any[], arr2: any[]): boolean
```
例如:
```js
isEqualArr([1,2,3], [1,2,3]) // true
isEqualArr([1,2,3],[1,3,2]) // true
```

## isEqual
简单地判断对象是否相等
```js
isEqual (a: any, b: any): boolean
```
例如:
```js
isEqual({name:'sichen'},{name:'sichen'}) // true
```

## shouldRender
```js
shouldRender (targetComponent: any):boolean
```

## appInfo
输出应用版本以及运维信息
```js
appInfo()
```

## mock
数据Mock
```js
// param {Object} params
mock (params: any)
```
