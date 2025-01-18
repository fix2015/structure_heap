# Heap Data Structure in JavaScript 🚀  

A simple implementation of the **Heap** data structure in JavaScript. This repository demonstrates how to create a heap class with essential methods and explains its functionality with practical examples.  

---

## What is a Heap?  
A **Heap** is a special tree-based data structure that satisfies the **heap property**. In a **Max Heap**, the value of each parent node is greater than or equal to the values of its children, while in a **Min Heap**, the value of each parent node is less than or equal to the values of its children. Heaps are commonly used to implement priority queues.  

---

## Features  
- **Insert**: Add a new element to the heap.  
- **Extract**: Remove and return the root element (max or min).  
- **Peek**: View the root element without removing it.  
- **Size**: Get the number of elements in the heap.  
- **Heapify**: Maintain the heap property after insertions or deletions.  

---

## Code Implementation  

Here’s the JavaScript implementation of the heap:  

```javascript
class Heap {
    constructor(type = "max") {
        this.type = type; // "max" for Max Heap, "min" for Min Heap
        this.heap = [];
    }

    // Insert an element into the heap
    insert(value) {
        this.heap.push(value);
        this.heapifyUp();
    }

    // Helper function to maintain the heap property after insertion
    heapifyUp() {
        let index = this.heap.length - 1;
        while (index > 0) {
            const parentIndex = Math.floor((index - 1) / 2);
            if (this.compare(this.heap[index], this.heap[parentIndex])) {
                [this.heap[index], this.heap[parentIndex]] = [this.heap[parentIndex], this.heap[index]];
                index = parentIndex;
            } else {
                break;
            }
        }
    }

    // Extract the root element (max or min)
    extract() {
        if (this.size() === 0) return null;
        const root = this.heap[0];
        const last = this.heap.pop();
        if (this.size() > 0) {
            this.heap[0] = last;
            this.heapifyDown();
        }
        return root;
    }

    // Helper function to maintain the heap property after extraction
    heapifyDown() {
        let index = 0;
        const length = this.heap.length;
        const leftChildIndex = (index * 2) + 1;
        const rightChildIndex = (index * 2) + 2;
        let swap = null;

        if (leftChildIndex < length) {
            if (this.compare(this.heap[leftChildIndex], this.heap[index])) {
                swap = leftChildIndex;
            }
        }
        if (rightChildIndex < length) {
            if (this.compare(this.heap[rightChildIndex], this.heap[swap || index])) {
                swap = rightChildIndex;
            }
        }
        if (swap === null) return;
        [this.heap[index], this.heap[swap]] = [this.heap[swap], this.heap[index]];
        this.heapifyDown();
    }

    // Compare two values based on the heap type
    compare(child, parent) {
        if (this.type === "max") {
            return child > parent;
        }
        return child < parent;
    }

    // Peek at the root element without removing it
    peek() {
        return this.heap[0];
    }

    // Get the size of the heap
    size() {
        return this.heap.length;
    }
}
```

---

## Example Usage  

```javascript
// Initialize a Max Heap
const maxHeap = new Heap("max");

// Insert elements into the heap
maxHeap.insert(10);
maxHeap.insert(20);
maxHeap.insert(5);

// Peek at the root element
console.log(maxHeap.peek()); // Output: 20

// Extract the root element (max)
console.log(maxHeap.extract()); // Output: 20
console.log(maxHeap.peek()); // Output: 10

// Get the size of the heap
console.log(maxHeap.size()); // Output: 2

// Initialize a Min Heap
const minHeap = new Heap("min");

// Insert elements into the min heap
minHeap.insert(10);
minHeap.insert(20);
minHeap.insert(5);

// Peek at the root element
console.log(minHeap.peek()); // Output: 5

// Extract the root element (min)
console.log(minHeap.extract()); // Output: 5
console.log(minHeap.peek()); // Output: 10
```

---

## Real-World Applications  
1. **Priority Queues**: For scheduling tasks based on priority.  
2. **Heap Sort**: Sorting an array in ascending or descending order.  
3. **Dijkstra’s Algorithm**: For finding the shortest path in a graph.  
4. **Dynamic Median Finding**: Finding the median in a dynamic data set.  

---

## TikTok Tutorial 🎥  
Want to see a quick tutorial on how to build this? Check out this TikTok video:  
[]()  

---

## How to Run the Code  
1. Clone the repository:  
   ```bash
   git clone https://github.com/fix2015/structure_heap
   cd structure_heap
   ```
2. Open the file `index.js` in your favorite code editor.  
3. Run the file using Node.js:  
   ```bash
   node index.js
   ```

---

## Contributing  
Contributions are welcome! If you have suggestions or want to add new features, feel free to create a pull request.  

---

## License  
This project is licensed under the MIT License.  

---

## Connect with Me:
- [LinkedIn - Vitalii Semianchuk](https://www.linkedin.com/in/vitalii-semianchuk-9812a786/)
- [Telegram - @jsmentorfree](https://t.me/jsmentorfree) - We do a lot of free teaching on this channel! Join us to learn and grow in web development.
- [Tiktok - @jsmentoring](https://www.tiktok.com/@jsmentoring) Everyday new videos
- [Youtube - @jsmentor-uk](https://www.youtube.com/@jsmentor-uk) Mentor live streams
- [Dev.to - fix2015](https://dev.to/fix2015) Javascript featured, live, experience but about Heap
