---
created: 2023-08-01 02:49:04
---

- https://leetcode.com/problems/valid-parentheses/

python
```python
def isValid(s):
    if s is None or len(s) == 0:
        return True

    stack = []
    for cha in s:
        if cha in ['(', '[', '{']:
            stack.append(cha)
        else:
            if not stack:
                return False
            last = stack.pop()
            if (cha == ')' and last != '(') or (cha == ']' and last != '[') or (cha == '}' and last != '{'):
                return False
    return len(stack) == 0

```

cpp
```cpp
#include <stack>
#include <string>

bool isValid(std::string s) {
    if (s.empty()) {
        return true;
    }
    std::stack<char> stack;
    for (char& cha : s) {
        if (cha == '(' || cha == '[' || cha == '{') {
            stack.push(cha);
        } else {
            if (stack.empty()) {
                return false;
            }
            char last = stack.top();
            stack.pop();
            if ((cha == ')' && last != '(') || (cha == ']' && last != '[') || (cha == '}' && last != '{')) {
                return false;
            }
        }
    }
    return stack.empty();
}

```


