### Longest Substring Without Repeating Characters

Given a string `s`, find the length of the **longest substring** without repeating characters.

 

**Example 1:**

```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

**Example 2:**

```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**

```
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

**Example 4:**

```
Input: s = ""
Output: 0
```

 

**Constraints:**

- `0 <= s.length <= 5 * 104`
- `s` consists of English letters, digits, symbols and spaces.

**solution:**

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    if(!s){
       return 0;
    }
    let set = new Array();
    let arr = s.split("");
    let max = 0;
    for (let i=0;i<arr.length;i++) {
        let index = set.indexOf(arr[i]);
        if(index>-1){
           max = max>set.length?max:set.length;
           set = cleanRepeat(set,index)
        } 
        set[set.length]= arr[i] ;
    }
    max = max>set.length?max:set.length;
    return max;
};

function cleanRepeat(set, index){
    
    return set.splice(index+1);
}
```

