---
created: 2023-07-18 05:52:41
---

# Python 🐍
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        if s is None or s == "":
            return 0
        str = list(s)
        map = [-1] * 256
        len = 0 # to collect the ans
        # pre: subarray ending as i-1, how much it can push to the left? record the position 
        # initialize as -1
        pre = -1
        cur = 0
        for i in range(len(str)):
            # obtain pre(i) from pre(i-1)
            pre = max(pre, map[ord(str[i])])
            cur = i - pre
            len = max(len, cur)
            map[ord(str[i])] = i
        return len

```
# C++🐦

```cpp
#include<vector>
#include<string>
#include<algorithm>

class Solution {
public:
    int lengthOfLongestSubstring(std::string s) {
        if (s.empty()) {
            return 0;
        }
      
		//int map[256]; std::fill(map, map+256, -1);
        std::vector<int> map(256, -1);
        int len = 0;
        int pre = -1;
        int cur = 0;
        for (int i = 0; i < s.size(); i++) {
            pre = std::max(pre, map[s[i]]);
            cur = i - pre;
            len = std::max(len, cur);
            map[s[i]] = i;
        }
        return len;
    }
};
```

# 🦀️ Rust
```rust
impl Solution {
    pub fn length_of_longest_substring(s: String) -> i32 {
        if s.is_empty(){
            return 0;
        }
        let str: Vec<char> = s.chars().collect();
        let mut map: Vec<i32> = vec![-1;256];
        let (mut len, mut pre, mut cur) = (0, -1, 0);
        for i in 0..str.len(){
            pre = pre.max(map[str[i] as usize]);
            cur = i as i32 - pre;
            len = len.max(cur);
            map[str[i] as usize] = i as i32;
        }
        return len;
    }
}
```f
fdsf