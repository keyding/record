## ES6 数组去重方法

1. 利用Set和Array.from

	Array.from(new Set([1,1,2,2,3,3,4,4])); // [1,2,3,4]

2. 利用解构

	let resultArr = [...new Set([1,1,2,2,3,3,4,4])]; // [1,2,3,4]md