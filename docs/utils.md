# Utils
导入
````js
  import { Utils } form 'dt-utils';
````
## pageWidth
获取页面宽度
```js
  Utils.pageWidth()
```
## pageHeight
获取页面高度
```js
  Utils.pageHeight()
```
## checkExist
检查属性是否存在
```js
  Utils.checkExist()
```
eg:
```js
  Utils.checkExist('') // false
  Utils.checkExist(null) // false
  Utils.checkExist(undefined) // false
```
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

eg:
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
eg:

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
eg:

````js
  let styles = {
    height:'100px',
    width:'100px',
    color:'red'
  }
  Utils.getCssText(styles); // 'height:100px;width:100px;color:red;'
````

## formatDateTime
 格式：`YYYY-MM-DD HH:mm:ss`

```js
  /**
   * @param {(string | number | Date)} timestap
   * @returns
   */
   Utils.formatDateTime (timestap: string | number | Date); 
```
eg:
```js
   Utils.formatDateTime(); 
```

## formatDate
 格式：`YYYY-MM-DD`

```js
  /**
   * @param {(string | number | Date)} timestap
   * @returns
   */
   Utils.formatDate (timestap: string | number | Date); 
```
eg:
```js
   Utils.formatDate(); 
```
## formatDateHours
 格式：`YYYY-MM-DD HH:mm`

```js
  /**
   * @param {(string | number | Date)} timestap
   * @returns
   */
   Utils.formatDateHours (timestap: string | number | Date); 
```
eg:
```js
   Utils.formatDateHours(); 
```
## formatDayHours
 格式：`MM-DD HH:mm`

```js
  /**
   * @param {(string | number | Date)} timestap
   * @returns
   */
   Utils.formatDayHours (timestap: string | number | Date); 
```
eg:
```js
   Utils.formatDayHours(); 
```
## formatHours
 格式：`HH:mm`

```js
  /**
   * @param {(string | number | Date)} timestap
   * @returns
   */
   Utils.formatHours (timestap: string | number | Date); 
```
eg:
```js
   Utils.formatHours(); 
```
## formatMinute
 格式：`HH:mm:ss`

```js
  /**
   * @param {(string | number | Date)} timestap
   * @returns
   */
   Utils.formatMinute (timestap: string | number | Date); 
```
eg:
```js
   Utils.formatMinute(); 
```

````js
const utils = {
    /**
   * 去除空串
   */
    trim (str: string) {
        return typeof str === 'string'
            ? str.replace(/^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g, '')
            : str;
    },

    trimlr (str: string) {
        const res = str.replace(/^\s*/, ''); // 去左边
        return res.replace(/\s*$/, ''); // 去右边
    },

    removeAllSpaces (str: string) {
        return typeof str === 'string'
            ? str.replace(/\s*/g, '') // 去除全部空串
            : str;
    },

    /**
   * 原生 JavaScript 获取 cookie 值
   * @param name
   */
    getCookie (name: string) {
        const arr = document.cookie.match(
            new RegExp('(^| )' + name + '=([^;]*)(;|$)')
        );
        if (arr != null) { return unescape(decodeURI(arr[2])); }
        return null;
    },

    deleteCookie (name: string, domain?: string, path?: string) {
        const d = new Date(0);
        domain = domain ? `; domain=${domain}` : '';
        path = path || '/';
        document.cookie =
      name + '=; expires=' + d.toUTCString() + domain + '; path=' + path;
    },

    deleteAllCookies (domain: string, path: string) {
        const cookies = document.cookie.split(';');
        // eslint-disable-next-line @typescript-eslint/prefer-for-of
        for (let i = 0; i < cookies.length; i++) {
            if (cookies[i]) {
                this.deleteCookie(cookies[i].split('=')[0], domain, path);
            }
        }
    },

    setCookie (name: string, value: string | number | object | boolean, days?: number) {
        let expires = '';
        if (days) {
            const date = new Date();
            date.setTime(date.getTime() + days * 24 * 60 * 60 * 1000);
            expires = '; expires=' + date.toUTCString();
        }
        document.cookie = name + '=' + value + expires + '; path=/';
    },

    /**
   * 转换 Byte 转换为小于1024值最大单位
   * @param value 'B' | 'KB' | 'MB' | 'GB' | 'TB' | 'PB' 转换原始值
   */
    convertBytes (value: number) {
        const units = ['B', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'];
        let i = 0;
        while (value >= 1024) {
            value = Number((value / 1024).toFixed(2));
            i++;
        }
        return `${value} ${units[i]}`;
    },

    /**
   * 时间转换 3661s--->1小时1分钟1秒
   */
    formatTime (time = 0) {
        let second = 0;
        let minute = 0;
        let hour = 0;

        function _formatHour (timestap: number) {
            hour = Math.floor(timestap / 3600);
            return timestap - hour * 3600;
        }
        function _formatMinute (timestap: number) {
            minute = Math.floor(timestap / 60);
            return timestap - minute * 60;
        }
        function _formatSecond (timestap: number) {
            second = timestap;
            return second;
        }
        _formatSecond(_formatMinute(_formatHour(time)));
        return `${hour ? hour + 'h' : ''}${minute ? minute + 'm' : ''}${second ? second + 's' : ''}` || '0s';
    },

    // 千位分割
    toQfw (str: string) {
        if (!str) {
            return 0;
        }
        str = str.toString ? str.toString() : str;
        const re = /(?=(?!(\b))(\d{3})+$)/g;
        str = str.replace(re, ',');
        return str;
    },
    // 文字溢出转换
    textOverflowExchange (text: string, length: number) {
        if (text && text.length > length) {
            return text.substring(0, length) + '...';
        }
        return text;
    },
    /**
   * json格式化
   * @param {格式化内容} text
   * @param {格式化占位符} space
   */
    jsonFormat (text: string, space?: number) {
        if (!text) {
            return text;
        }
        try {
            const json = JSON.parse(text);
            const output = JSON.stringify(json, null, space || 2);

            return output;
        } catch (e) {
            return null;
        }
    },
    /**
   * 多函数排序，匹配到0为止
   */
    sortByCompareFunctions (arr: any[], ...compareFunctions: any[]) {
        arr.sort((a, b) => {
            let result = 0;
            for (const func of compareFunctions) {
                result = func(a, b);
                if (result !== 0) {
                    return result;
                }
            }
            return result;
        });
    },
    /**
   * 转换排序字段
   */
    exchangeOrder (order: string) {
        switch (order) {
            case 'ascend':
                return 'asc';
            case 'descend':
                return 'desc';
            default:
                return undefined;
        }
    },
    /**
   * 生成一个key
   */
    generateAKey () {
    // tslint:disable-next-line:no-bitwise
        return '' + new Date().getTime() + ~~(Math.random() * 1000000);
    },

    /**
   * 判断是否是JSON string
   * @param  {String}  str 所要验证的字符串
   * @return {Boolean}   是否是JSON字符串
   */
    isJSONStr (str: string) {
        str = this.trimlr(str);
        return (
            (str.charAt(0) === '{' && str.charAt(str.length - 1) === '}') ||
      (str.charAt(0) === '[' && str.charAt(str.length - 1) === ']')
        );
    },
    /**
   * 随机生成一串6位同时包含数字、大小写字母的字符串
   * @param len number
   */
    getRandomStr (len: number): string {
        const numChar = '0123456789';
        const lowerCaseChar = 'abcdefghijklmnopqrstuvwxyz';
        const upperCaseChar = 'ABCDEFGHIJKLMNOPQRSTUVXYZ';
        function getChar (baseChar: string) {
            const randomIndex = Math.random() * (baseChar.length - 1);
            return baseChar.charAt(randomIndex);
        }
        let currentChar = 'num';
        let str = '';
        for (let i = 0; i < len; i++) {
            if (currentChar === 'num') {
                str += getChar(numChar);
                currentChar = 'lower';
            } else if (currentChar === 'lower') {
                str += getChar(lowerCaseChar);
                currentChar = 'upper';
            } else if (currentChar === 'upper') {
                str += getChar(upperCaseChar);
                currentChar = 'num';
            }
        }
        return str;
    },
    /**
   * simply judge whether the array is equal
   * @param arr1
   * @param arr2
   * @returns arr1 === arr2
   */
    isEqualArr (arr1: string[], arr2: string[]): boolean {
        const toString = JSON.stringify;
        return toString(arr1.sort()) === toString(arr2.sort());
    },
    /**
     *
     *
     * @param {*} a
     * @param {*} b
     * @returns boolean
     */
    isEqual (a: any, b: any): boolean {
        for (const key in a) {
            if ({}.hasOwnProperty.call(a, key) &&
        (!{}.hasOwnProperty.call(b, key) || a[key] !== b[key])) {
                return false;
            }
        }
        for (const key in b) {
            if ({}.hasOwnProperty.call(b, key) && !{}.hasOwnProperty.call(a, key)) {
                return false;
            }
        }
        return true;
    },
    /**
     *
     *
     * @param {*} targetComponent
     */
    shouldRender (targetComponent: any) {
        targetComponent.prototype.shouldComponentUpdate = function (props: any, state: any) {
            return !this.isEqual(this.state, state) || !this.isEqual(this.props, props);
        };
    },
    /**
     *
     * 输出应用版本以及运维信息
     */
    appInfo () {
        window.console.log(`%cApp current version: v${APP.VERSION}`, 'font-family: Cabin, Helvetica, Arial, sans-serif;text-align: left;font-size:32px;color:#B21212;');
    },
    /**
     * 数据Mock
     * @param {Object} params
     */
    mock (params: any) {
        return function (target: any, name: any, descriptor: any) {
            console.log('target:', target, name, descriptor);
            for (const props in params) {
                if (target[props]) {
                    target[props] = params[props];
                }
            }
        };
    },
};
````