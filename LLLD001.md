## 知识点
- 栈
- 空间换时间

## 剑指 Offer 09.用两个栈实现队列 LCOF
```js
var CQueue = function () {
  this.stack1 = [];
  this.stack2 = [];
};

CQueue.prototype.appendTail = function (value) {
  this.stack1.push(value);
};

CQueue.prototype.deleteHead = function () {
  if (this.stack2.length === 0) {
    while (this.stack1.length) {
      this.stack2.push(this.stack1.pop());
    }
  }
  if (this.stack2.length === 0 && this.stack1.length === 0) {
    return -1;
  } else {
    var result = this.stack2.pop();
    return result;
  }
};
```
## 剑指 Offer 30.包含min函数的栈 LCOF
```js
/**
 * initialize your data structure here.
 */
var MinStack = function () {
  this.stack1 = [];
  this.stack2 = [];
  this.topIndex = -1;
  this.minIndex = -1;
};

/**
 * @param {number} x
 * @return {void}
 */
MinStack.prototype.push = function (x) {
  var min = this.stack2[this.minIndex];
  if (this.minIndex === -1 || min >= x) {
    this.minIndex += 1;
    this.stack2.push(x);
  }

  this.stack1.push(x);
  this.topIndex += 1;
};

/**
 * @return {void}
 */
MinStack.prototype.pop = function () {
  var stack1Top = this.stack1.pop();
  var min = this.stack2[this.minIndex];

  this.topIndex -= 1;

  if (stack1Top === min) {
    this.stack2.pop();
    this.minIndex -= 1;
  }
};

/**
 * @return {number}
 */
MinStack.prototype.top = function () {
  if (this.topIndex === -1) {
    return null;
  }
  return this.stack1[this.topIndex];
};

/**
 * @return {number}
 */
MinStack.prototype.min = function () {
  return this.stack2[this.minIndex];
};
/**
 * Your MinStack object will be instantiated and called as such:
 * var obj = new MinStack()
 * obj.push(x)
 * obj.pop()
 * var param_3 = obj.top()
 * var param_4 = obj.min()
 */
 ```