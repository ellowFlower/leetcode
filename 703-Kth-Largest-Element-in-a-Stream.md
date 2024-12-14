# 703. Kth Largest Element in a Stream

The min heap data structure stores the elements in a descending order. Adding elements and seeing the kth largest can be done in an efficient way.

## Code
```go
import (
	"github.com/emirpasic/gods/v2/queues/priorityqueue"
)

type KthLargest struct {
	k       int
	minHeap *priorityqueue.Queue[int]
}

func IntComparator(a, b int) int {
	switch {
	case a < b:
		return -1
	case a > b:
		return 1
	default:
		return 0
	}
}

func Constructor(k int, nums []int) KthLargest {
	minHeap := priorityqueue.NewWith[int](IntComparator)
	for _, num := range nums {
		minHeap.Enqueue(num)
	}
	for minHeap.Size() > k {
		minHeap.Dequeue()
	}
	return KthLargest{k: k, minHeap: minHeap}
}

func (this *KthLargest) Add(val int) int {
	this.minHeap.Enqueue(val)
	if this.minHeap.Size() > this.k {
		this.minHeap.Dequeue()
	}
	result, _ := this.minHeap.Peek()
	return result
}

/**
 * Your KthLargest object will be instantiated and called as such:
 * obj := Constructor(k, nums);
 * param_1 := obj.Add(val);
 */
```
