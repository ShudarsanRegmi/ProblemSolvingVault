# Best Time to Buy and Sell Stock

Easy

You are given an integer array `prices` where `prices[i]` is the price of NeetCoin on the `ith` day.

You may choose a **single day** to buy one NeetCoin and choose a **different day in the future** to sell it.

Return the maximum profit you can achieve. You may choose to **not make any transactions**, in which case the profit would be `0`.

**Example 1:**

```java
Input: prices = [10,1,5,6,7,1]

Output: 6
```


Explanation: Buy `prices[1]` and sell `prices[4]`, `profit = 7 - 1 = 6`.

**Example 2:**

```java
Input: prices = [10,8,7,5,2]

Output: 0
```


Explanation: No profitable transactions can be made, thus the max profit is 0.

**Constraints:**

- `1 <= prices.length <= 100`
- `0 <= prices[i] <= 100`

---
![[SlidingWindow/SlidingWindow.excalidraw.md#^group=2gdJnykz7EcHafouRjyxI|100%]]

## Algorithm

![[SlidingWindow/SlidingWindow.excalidraw.md#^group=I0OPOXwD_I6y9VHOgDAey|100%]]

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int min = prices[0];
        int  max = prices[0];
        int profit = 0;
        int maxProfit = 0;
        for (int i=0; i<prices.size(); i++) {
            if(prices[i]<min) {
                min = prices[i];
                max = min;
            }
            if(prices[i]>max) {
                max = prices[i];
            }
            profit = max-min;
            if(profit>maxProfit){
                maxProfit = profit;
            }
        }
        return maxProfit;
    }
};
```
