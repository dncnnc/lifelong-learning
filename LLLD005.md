# 【程序员终身学习】D5｜剑指 Offer 学习

## 剑指 Offer 04. 二维数组中的查找

```jsx
/**
 * @param {number[][]} matrix
 * @param {number} target
 * @return {boolean}
 */
var findNumberIn2DArray = function (matrix, target) {
  if (!matrix.length) {
    return false;
  }

  var row = 0;
  var column = matrix[0].length - 1;
  var result = false;

  while (row <= matrix.length - 1 && column >= 0) {
    var num = matrix[row][column];
    if (num > target) {
      column -= 1;
    } else if (num < target) {
      row += 1;
    } else {
      result = true;
      break;
    }
  }
  return result;
};
```

## 剑指 Offer 11. 旋转数组的最小数字

```jsx
/**
 * @param {number[]} numbers
 * @return {number}
 */
var minArray = function(numbers) {

};
```

## 剑指 Offer 50. 第一个只出现一次的字符

```jsx
/**
 * @param {string} s
 * @return {character}
 */
var firstUniqChar = function (s) {
  if (!s) {
    return " ";
  }
  const map = new Map();

  for (var str of s) {
    if (map.has(str)) {
      map.set(str, -1);
    } else {
      map.set(str, 1);
    }
  }

  for (var str2 of s) {
    if (map.get(str2) == 1) {
      return str2;
    }
  }
  return " ";
};
```