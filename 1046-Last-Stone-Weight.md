## 1046. Last Stone Weight
Store the values in a min heap to have them sorted. Then get always the highest two values and do the needed calculation on it.

## Code
```go
import (
	"github.com/emirpasic/gods/v2/queues/priorityqueue"
)

func main() {
	lastStoneWeight([]int{3, 7, 2})
}

type KthLargest struct {
	k       int
	minHeap *priorityqueue.Queue[int]
}

// Comparator function for integers
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

func lastStoneWeight(stones []int) int {
    if (len(stones) == 1) {
        return stones[0]
    }

    // store stones in descending order
    minHeap := priorityqueue.NewWith[int](IntComparator)
	for _, s := range stones {
        // save negative to have maxHeap and be able to get 2 largest elements below
		minHeap.Enqueue(-s)
	}
	
    for minHeap.Size() >= 2 {
        // get 2 largest elements and compare them
        x, _ := minHeap.Dequeue()
        y, _ := minHeap.Dequeue()

        if (x != y) {
            minHeap.Enqueue(x-y)
        }
    }

    if (minHeap.Size() > 0) {
        r, _ := minHeap.Dequeue()
        return r * -1
    }
    return 0
}
```
