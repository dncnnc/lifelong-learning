## 知识点

### 链表

链表是一种常见的基础数据结构。在链表中，每个节点包含指向下一个节点的指针，这些指针把节点连接成链状结构。

### 回溯法

回溯法可以看作蛮力法的升级版，它在解决问题时的每一步都尝试所有可能的选项，最终找出所有可行的解决方案。回溯法非常适合解决由多个步骤组成的问题，并且每个步骤都有多个选项。在某一步选择了其中一个选项之后，就进入下一步，然后会面临新的选项。就这样重复选择，直至到达最终的状态。

### 哈希表

哈希表是一种常见的数据结构，在解决算法面试题的时候经常需要用到哈希表。哈希表最大的优点是高效，在哈希表中插入、删除或查找一个元素都只需要O（1）的时间。因此，哈希表经常被用来优化时间效率。

## 剑指 Offer 06. 从尾到头打印链表

耗时：30min

```jsx
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {number[]}
 */
var reversePrint = function (head) {
  const stack = [];
  const result = [];
  let curNode = head;

  while (curNode !== null) {
    stack.push(curNode.val);
    curNode = curNode.next;
  }

  while (stack.length) {
    result.push(stack.pop());
  }

  return result
};
```

## 剑指 Offer 24. 反转链表

耗时：15min剑指 Offer 35. 复杂链表的复制

```jsx
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var reverseList = function (head) {
  var prev = null;
  var cur = head;

  while (cur !== null) {
    var next = cur.next;
    cur.next = prev;
    prev = cur;
    cur = next;
  }
  return prev;
};
```

## 剑指 Offer 35. 复杂链表的复制

耗时：75min

```jsx
/**
 * // Definition for a Node.
 * function Node(val, next, random) {
 *    this.val = val;
 *    this.next = next;
 *    this.random = random;
 * };
 */

/**
 * @param {Node} head
 * @return {Node}
 */

var copyRandomList = function (head) {
  var node = head;
  var map = new Map();

  if (!head) {
    return head;
  }

  while (node) {
    map.set(node, new Node(node.val));
    node = node.next;
  }

  node = head;

  while (node) {
    map.get(node).next = map.get(node.next) === undefined ? null : map.get(node.next);
    map.get(node).random = map.get(node.random);
    node = node.next;
  }

  return map.get(head)
};
```