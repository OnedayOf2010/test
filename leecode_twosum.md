## Two Sum
> 给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。

 你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。

 你可以按任意顺序返回答案。

// 来源：力扣（LeetCode）
// 链接：https://leetcode-cn.com/problems/two-sum
// 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。


* 示例 1：

  输入：nums = [2,7,11,15], target = 9
 输出：[0,1]
 解释：因为 nums[0] + nums[1] == 9 ，返回 [0, 1] 。
 * 示例 2：

 输入：nums = [3,2,4], target = 6
 输出：[1,2]
 示例 3：

 输入：nums = [3,3], target = 6
 输出：[0,1]

```javascript


/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
function twoSum(nums, target) {
    let obj = {}, len = nums.length;
    for (let i = 0; i < len; i++) {
        let temp = obj[target - nums[i]];
        if (temp === undefined) {

            obj[target - nums[i]] = i;
        } else {
            obj[target - nums[i]] = [temp, i];
        }
    }
    for (let j = 0; j < len; j++) {
        let temp1 = obj[nums[j]];
        if (temp1 !== undefined && temp1 !== j) {
            if (Array.isArray(temp1)) {
                let rs = temp1.filter((a) => { return a !== j })
                return [j,rs[0]];
            } else {
                return [j, obj[nums[j]]];
            }
        }
    }
    return null;
}
```
