# 【程序员终身学习】D4｜剑指 Offer 学习

## 剑指 Offer 03. 数组中重复的数字

```jsx
/**
 * @param {number[]} nums
 * @return {number}
 */
var findRepeatNumber = function (nums) {
  var len = nums.length;
  var i = 0;
  var map = new Map();
  var result;
  for (i; i < len; i++) {
    if (map.has(nums[i])) {
      result = nums[i];
      break;
    }
    map.set(nums[i]);
  }

  return result;
};
```

## 剑指 Offer 53 - I. 在排序数组中查找数字 I

```jsx
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var binarySearch = function (nums, target, lower) {
  var left = 0;
  var right = nums.length - 1;
  var result = nums.length;

  while (left <= right) {
    var mid = Math.floor((right + left) / 2);
    if (nums[mid] > target || (lower && nums[mid] >= target)) {
      right = mid - 1;
      result = mid;
    } else {
      left = mid + 1;
    }
  }

  return result;
};
var search = function (nums, target) {
  var lower = binarySearch(nums, target, true);
  var higher = binarySearch(nums, target, false) - 1;

  if (
    higher >= lower &&
    nums[higher] === target &&
    nums[lower] === target &&
    higher < nums.length
  ) {
    return higher - lower + 1;
  }
  return 0;
};
```

## 剑指 Offer 53 - II. 0～n-1中缺失的数字剑指 Offer 03. 数组中重复的数字

```jsx
/**
 * @param {number[]} nums
 * @return {number}
 */
var missingNumber = function (nums) {
  var left = 0;
  var right = nums.length - 1;

  while (left <= right) {
    var mid = Math.floor((left + right) / 2);
    if (nums[mid] === mid) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }
  return left;
};
```