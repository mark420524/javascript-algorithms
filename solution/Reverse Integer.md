### Reverse Integer

Given a signed 32-bit integer `x`, return `x` *with its digits reversed*. If reversing `x` causes the value to go outside the signed 32-bit integer range [-2<sup>31</sup>, 2<sup>31</sup> - 1], then return `0`.

**Assume the environment does not allow you to store 64-bit integers (signed or unsigned).**

 

**Example 1:**

```
Input: x = 123
Output: 321
```

**Example 2:**

```
Input: x = -123
Output: -321
```

**Example 3:**

```
Input: x = 120
Output: 21
```

**Example 4:**

```
Input: x = 0
Output: 0
```

 

**Constraints:**

- -2<sup>31</sup> <= x <= 2<sup>31</sup> - 1

**solution:**

```javascript
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
	let MIN = 1<<31 ;
    let MAX = (1<<30)*2-1
    let negative = x<0;
	let result = 0;
	while (x!=0)
	{
		let a = x % 10 ;
		x  = parseInt(x/10);
		result = result * 10 + a;
		if(result>MAX || result<MIN){
           result = 0;
           break;
        }
	}
    return result;
};
```



