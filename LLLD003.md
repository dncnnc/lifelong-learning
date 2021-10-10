# 【程序员终身学习】D3｜剑指 Offer 学习

## 剑指 Offer 05. 替换空格

```jsx
/**
 * @param {string} s
 * @return {string}
 */
var replaceSpace = function (s) {
  return s.replace(/\s/g, "%20");
};
```

## 剑指 Offer 58 - II. 左旋转字符串

```jsx
/**
 * @param {string} s
 * @param {number} n
 * @return {string}
 */
var reverseLeftWords = function (s, n) {
  var start = "";
  var end = "";

  s.split("").forEach((char, index) => {
    if (index < n) {
      start += char;
    } else {
      end += char;
    }
  });
  return end + start;
};
```