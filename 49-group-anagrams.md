# 49. Group Anagrams
First, group all anagrams together by the occurence amount of every letter within the input words. From that construct the desired output of a list containing sublists of all anagrams.

## Code
```go
func groupAnagrams(strs []string) [][]string {
    // key: list of letter count, value: list of anagrams
    groupedAnagrams := make(map[[26]int][]string)
    
    for _,s := range strs {
        // index 0 represents a; index 25 represents z
        var letterCount [26]int
        for _,c := range s {
            letterCount[c-'a']++    
        }
        groupedAnagrams[letterCount] = append(groupedAnagrams[letterCount], s)
    }

    var groupedAnagramsList [][]string
    for _,v := range groupedAnagrams {
        groupedAnagramsList = append(groupedAnagramsList, v)
    }
    return groupedAnagramsList
}
```
