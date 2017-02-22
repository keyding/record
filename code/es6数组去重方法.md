## ES6 数组去重方法

- 利用Set和Array.from

```javascript
Array.from(new Set([1,1,2,2,3,3,4,4])); // [1,2,3,4]
```

- 利用解构

```javascript
let resultArr = [...new Set([1,1,2,2,3,3,4,4])]; // [1,2,3,4]md
```