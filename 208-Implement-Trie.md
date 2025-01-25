# 208. Implement Trie (Prefix Tree)

Implementation of the whole trie data structure.

## Code
```go
type TrieNode struct {
    children [26]*TrieNode
    endOfWord bool 
 }
 
 type Trie struct {
     root *TrieNode
 }
 
 
 func Constructor() Trie {
    return Trie{root: &TrieNode{}}
 }
 
 
 func (this *Trie) Insert(word string)  { 
     cur := this.root
     for _, c := range word {
         i := c - 'a'
         if cur.children[i] == nil {
             cur.children[i] = &TrieNode{}
         }
         cur = cur.children[i]
     }
     cur.endOfWord = true
 }
 
 
 func (this *Trie) Search(word string) bool {
     cur := this.root
     for _, c := range word {
         i := c - 'a'
         if cur.children[i] == nil {
             // next char in word not present
             return false
         }
         cur = cur.children[i]
     }
    return cur.endOfWord
 }
 
 
 func (this *Trie) StartsWith(prefix string) bool {
     cur := this.root
     visited := 0
     for _, c := range prefix {
         i := c - 'a'
         if cur.children[i] == nil {
             // next char in word not present
             return false
         }
         cur = cur.children[i]
         visited++
     }
    return true
 }
 
 
 /**
  * Your Trie object will be instantiated and called as such:
  * obj := Constructor();
  * obj.Insert(word);
  * param_2 := obj.Search(word);
  * param_3 := obj.StartsWith(prefix);
  */

```
