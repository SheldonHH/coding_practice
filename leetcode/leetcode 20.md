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


