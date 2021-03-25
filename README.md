1. (Easy) Two Sum

* O(n) Time (Better)

找出 array裡的號碼 相加起來等於 target 號碼的 index

``` javascript
var twoSum = function(nums, target) {
    let result = {};

    for(let i = 0; i < nums.length; i++) {
        let thisNum = nums[i];
        result[thisNum] = i
    }

    for(let i = 0; i < nums.length; i++) {
        let diff = target - nums[i];
        if(result.hasOwnProperty(diff) && result[diff] !== i) {
            return [i, result[diff]]
        }
    }
const nums = [2, 7, 11, 15];
const target = 9;
twoSum(nums, target)
```

``` javascript
// 第一輪 loop 做一個 寫的 obj
let result = { // value: index
  -6: 2,
  15: 0,
  2: 3,
  7: 1
}
```

上面需要注意的事 **diff = target - nums[i]**
1. target 是 9
2. 它減了 array裡的號碼 得到了 diff = 相差值
3. 就是說 那個 diff 的value 其實是 他要找的 value
4. **result.hasOwnProperty(diff)** 還記得 我們的Obj的key 是 value嗎
5. 所以 他去找了 result裡的 key 有沒有 這個diff， 有的話 就是 他的目標了
6. 過後 它就會 return 當前的 i (因為 它只loop在這裡， 然後obj 裡又有這個key value)
7. 和 result[diff] 的 obj value 也就是 index
Note: 其實它 不是去找 target 的號碼 它是去找diff的號碼， 也就是說 有bug， 如果 那個diff號碼 也有在 obj裡 那樣 就會發生 bug了，除非+多一個 if condition target === 9

* O(n^2) Time

``` javascript
var twoSum = function(nums, target) {
    let result = [];

    for(let i = 0; i < nums.length; i++) {
        for(let j = i + 1; j < nums.length; j++) {
            if(nums[i] + nums[j] === target) {
                result.push(i);
                result.push(j);
            }
        }
    }
    return result;
};

const nums = [2, 7, 11, 15];
const target = 9;
twoSum(nums, target)
```