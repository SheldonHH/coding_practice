---
created: 2023-08-01 10:05:27
---

# Java
```java
public class Problem_0029_DivideTwoIntegers {

	public static int add(int a, int b) {
		int sum = a;
		while (b != 0) {
			sum = a ^ b;
			b = (a & b) << 1;
			a = sum;
		}
		return sum;
	}

	public static int negNum(int n) {
		return add(~n, 1);
	}

	public static int minus(int a, int b) {
		return add(a, negNum(b));
	}

	public static int multi(int a, int b) {
		int res = 0;
		while (b != 0) {
			if ((b & 1) != 0) {
				res = add(res, a);
			}
			a <<= 1;
			b >>>= 1;
		}
		return res;
	}

	public static boolean isNeg(int n) {
		return n < 0;
	}

	public static int div(int a, int b) {
		int x = isNeg(a) ? negNum(a) : a;
		int y = isNeg(b) ? negNum(b) : b;
		int res = 0;
		for (int i = 31; i > negNum(1); i = minus(i, 1)) {
			if ((x >> i) >= y) {
				res |= (1 << i);
				x = minus(x, y << i);
			}
		}
		return isNeg(a) ^ isNeg(b) ? negNum(res) : res;
	}

	public static int divide(int dividend, int divisor) {
		if (divisor == Integer.MIN_VALUE) {
			return dividend == Integer.MIN_VALUE ? 1 : 0;
		}
		// 除数不是系统最小
		if (dividend == Integer.MIN_VALUE) {
			if (divisor == negNum(1)) {
				return Integer.MAX_VALUE;
			}
			int res = div(add(dividend, 1), divisor);
			return add(res, div(minus(dividend, multi(res, divisor)), divisor));
		}
		// dividend不是系统最小，divisor也不是系统最小
		return div(dividend, divisor);
	}
	// div(a,b) a和b都不能是系统最小

	// 现场福利函数
	public static String printNumBinary(int num) {
		StringBuilder builder = new StringBuilder();
		for (int i = 31; i >= 0; i--) {
			builder.append(((num >> i) & 1) == 0 ? '0' : '1');
		}
		return builder.toString();
	}

	public static void main(String[] args) {
		int num = -1;
		System.out.println(printNumBinary(num));
	}

}
```

Python
```python
def add(a, b):
    sum = a
    while b != 0:
        sum = a ^ b
        b = (a & b) << 1
        a = sum
    return sum

def neg_num(n):
    return add(~n, 1)

def minus(a, b):
    return add(a, neg_num(b))

def multi(a, b):
    res = 0
    while b != 0:
        if (b & 1) != 0:
            res = add(res, a)
        a <<= 1
        b >>= 1
    return res

def is_neg(n):
    return n < 0

def div(a, b):
    x = neg_num(a) if is_neg(a) else a
    y = neg_num(b) if is_neg(b) else b
    res = 0
    for i in range(31, neg_num(1)-1, -1):
        if (x >> i) >= y:
            res |= (1 << i)
            x = minus(x, y << i)
    return neg_num(res) if is_neg(a) ^ is_neg(b) else res

def divide(dividend, divisor):
    min_int, max_int = -2**31, 2**31 - 1
    if divisor == min_int:
        return 1 if dividend == min_int else 0
    if dividend == min_int:
        if divisor == neg_num(1):
            return max_int
        res = div(add(dividend, 1), divisor)
        return add(res, div(minus(dividend, multi(res, divisor)), divisor))
    return div(dividend, divisor)

def print_num_binary(num):
    return ''.join(['1' if ((num >> i) & 1) != 0 else '0' for i in range(31, -1, -1)])

if __name__ == "__main__":
    num = -1
    print(print_num_binary(num))

```


# Python
```python
def add(a, b):
    sum = a
    while b != 0:
        sum = a ^ b
        b = (a & b) << 1
        a = sum
    return sum

def neg_num(n):
    return add(~n, 1)

def minus(a, b):
    return add(a, neg_num(b))

def multi(a, b):
    res = 0
    while b != 0:
        if (b & 1) != 0:
            res = add(res, a)
        a <<= 1
        b >>= 1
    return res

def is_neg(n):
    return n < 0

def div(a, b):
    x = neg_num(a) if is_neg(a) else a
    y = neg_num(b) if is_neg(b) else b
    res = 0
    for i in range(31, neg_num(1)-1, -1):
        if (x >> i) >= y:
            res |= (1 << i)
            x = minus(x, y << i)
    return neg_num(res) if is_neg(a) ^ is_neg(b) else res

def divide(dividend, divisor):
    min_int, max_int = -2**31, 2**31 - 1
    if divisor == min_int:
        return 1 if dividend == min_int else 0
    if dividend == min_int:
        if divisor == neg_num(1):
            return max_int
        res = div(add(dividend, 1), divisor)
        return add(res, div(minus(dividend, multi(res, divisor)), divisor))
    return div(dividend, divisor)

def print_num_binary(num):
    return ''.join(['1' if ((num >> i) & 1) != 0 else '0' for i in range(31, -1, -1)])

if __name__ == "__main__":
    num = -1
    print(print_num_binary(num))

```