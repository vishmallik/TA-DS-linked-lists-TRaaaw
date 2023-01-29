Using the linked list class you created in the previous exercise implement stack and queue:

- Implement Stack using the following methods
  - `add` Adds an element to the stack
  - `remove` Removes an element from the stack
  - `peek` returns the first element from the top of the stack
  - `printAll` print all the elements of the stack from one after another from the top
  - `isEmpty` Returns `true` if the stack is empty

**YOU HAVE TO USE LINKED LIST TO STORE DATA**

```js
class Node {
  constructor(element) {
    this.element = element;
    this.next = null;
  }
}

class LinkedList {
  constructor(head = null) {
    this.head = head ? new Node(head) : head;
    this.tail = this.head;
  }
  insertHead(element) {
    let node = new Node(element);
    if (this.head === null) {
      this.head = this.tail = node;
      return node;
    } else {
      let currentNode = this.head;
      node.next = currentNode;
      this.head = node;
      return node;
    }
  }
  removeHead() {
    if (this.head === null) {
      return false;
    } else {
      let currentNode = this.head;
      this.head = currentNode.next;
      return currentNode;
    }
  }
  insertTail(element) {
    let node = new Node(element);
    if (this.tail === null) {
      this.head = this.tail = node;
      return node;
    } else {
      this.tail.next = node;
      this.tail = node;
      return node;
    }
  }

  removeTail() {
    if (this.tail === null) {
      return false;
    } else {
      let tailNode = this.tail;
      let currentNode = this.head;
      let previousNode;
      while (currentNode.next) {
        previousNode = currentNode;
        currentNode = currentNode.next;
      }
      if (!previousNode) {
        this.tail = null;
        this.head = null;
        return tailNode;
      }
      previousNode.next = null;
      this.tail = previousNode;
      return tailNode;
    }
  }

  printAll() {
    let currentNode = this.head;
    let printOutput = "";
    while (currentNode) {
      printOutput = printOutput.concat(currentNode.element, ",");
      currentNode = currentNode.next;
    }
    console.log(printOutput.slice(0, -1));
  }
  forEach(cb) {
    let currentNode = this.head;
    while (currentNode) {
      cb(currentNode.element);
      currentNode = currentNode.next;
    }
  }
  get size() {
    let currentNode = this.head;
    let length = 0;
    while (currentNode) {
      length++;
      currentNode = currentNode.next;
    }
    return length;
  }
  find(cb) {
    let currentNode = this.head;
    while (currentNode) {
      if (cb(currentNode.element)) {
        return currentNode.element;
      }
      currentNode = currentNode.next;
    }
    return -1;
  }
}

class Stack {
  // your code goes here
  constructor() {
    this.storage = new LinkedList();
  }
  add(element) {
    this.storage.insertTail(element);
    return this.storage.size;
  }
  remove() {
    return this.storage.removeTail().element;
  }
  peek() {
    return this.storage.tail.element;
  }
  printAll() {
    this.storage.printAll().reverse();
  }
  isEmpty() {
    return this.storage.size === 0;
  }
  get length() {
    return this.storage.size;
  }
}

// Test 1

const stack = new Stack();

stack.add(10);
stack.add(12);
stack.add(120);
stack.add(1);
stack.add(4);

console.log(stack.remove()); // => 4
console.log(stack.length); // => 4
console.log(stack.remove()); // => 1
console.log(stack.length); // => 3

console.log(stack.peek()); // 120

console.log(stack.isEmpty()); // false

console.log(stack.remove()); // => 120

console.log(stack.add(100)); // 3

console.log(stack.peek()); // => 100

console.log(stack.remove()); // => 100
console.log(stack.remove()); // => 12
console.log(stack.remove()); // => 10

console.log(stack.isEmpty()); // true
```

- Implement Queue using the following methods
  - `enqueue` Add the element to the queue
  - `dequeue` Removes an element from the queue
  - `peek` returns the first element from the top of the queue
  - `printAll` print all the elements of the queue from one after another from the top
  - `isEmpty` Returns `true` if the queue is empty

**YOU HAVE TO USE LINKED LIST TO STORE DATA**

```js
class Queue {
  // your code goes here
  constructor() {
    this.storage = new LinkedList();
  }
  enqueue(element) {
    this.storage.insertTail(element);
    return this.storage.size;
  }
  dequeue() {
    return this.storage.removeHead().element;
  }
  peek() {
    return this.storage.head.element;
  }
  printAll() {
    this.storage.printAll().reverse();
  }
  isEmpty() {
    return this.storage.size === 0;
  }
  get length() {
    return this.storage.size;
  }
}

// Test 1

const queue = new Queue();

queue.enqueue(10);
queue.enqueue(12);
queue.enqueue(120);
queue.enqueue(1);
queue.enqueue(4);

console.log(queue.dequeue()); // => 10
console.log(queue.length); // => 4
console.log(queue.dequeue()); // => 12
console.log(queue.length); // => 3

console.log(queue.peek()); // 120

console.log(queue.isEmpty()); // false

console.log(queue.dequeue()); // => 120

console.log(queue.peek()); // => 1

console.log(queue.dequeue()); // => 1
console.log(queue.dequeue()); // => 4

console.log(queue.isEmpty()); // true
```
