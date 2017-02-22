## 用JS代码求出页面上一个元素的最终的background-color，不考虑IE浏览器，不考虑元素float情况。

```javascript
(function (N_M, undefined) {
	// 字符串转换为驼峰写法，如: 将background-color转换为backgroundColor
	function camelize(str) {
	    return str.replace(/-(\w)/g, function (strMatch, s1){
	        return s1.toUpperCase();
	    });
	}

	// 获取特定元素的计算样式
	function getStyle(elem, property) {
		if(!elem || !property) {
			return null;
		}

		// 获取是否有内联样式
		let value = elem.style[camelize(property)];

		// 如果无内联样式，则获取层叠样式表计算后的样式
		if(!value) {

			let doc_defaultView = document.defaultView;

			// document.defaultView.getComputedStyle 方法返回一个只读的CSSStyleDeclaration对象
			if(doc_defaultView && doc_defaultView.getComputedStyle) {

				// 获取的所有的计算样式
				let css = doc_defaultView.getComputedStyle(elem, null);

				value = css ? css.getPropertyValue(property) : null;
			}
		}

		return value;
	}

	// 检测获取的背景色是否有效
	function checkBgValue(elem) {

		let value = getStyle(elem, 'background-color');

		// 是否有背景颜色
		let hasBgColor = value ? true : false;

		// 排除一些特殊情况
		// 未设置background-color 或者 设置为跟随父节点 ^_^ value === 'rgba(0, 0, 0, 0)') 没有考虑rgb和特定颜色值（如red）的情况，待改进
		if(value === 'transparent' || value === 'rgba(0, 0, 0, 0)') {
			hasBgColor = false;
		}
		// DOM 节点透明度为全透明
		else if(getStyle(elem, 'opacity') === '0') {
			hasBgColor = false;
		}
		// DOM 节点不可见
		else if(getStyle(elem, 'visibility') === 'hidden') {
			hasBgColor = false;
		}
		// DOM 节点不可见
		else if(getStyle(elem, 'display') === 'none') {
			hasBgColor = false;
		}

		return hasBgColor;
	}

	// 获取元素在页面最终显示的颜色
	function getRealBgValue(elem) {
		// 如果直接获取到结果
		if(checkBgValue(elem)) {
			return getStyle(elem, 'background-color');
		}
		// 如果没有，递归查找父节点以及更上层的样式，获取肉眼能看到的，显示在页面上的background-color值
		// 如果已经查找到html根节点，则可以停止查找
		else if(elem != document.documentElement) {
			return getRealBgValue(elem.parentNode);
		}
	}

	N_M.getBgColor = getRealBgValue;
})(window.N_M || (window.N_M = {}));
```