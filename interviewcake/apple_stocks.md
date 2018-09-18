# Question

Writing programming interview questions hasn't made me rich yet ... so I might give up and start trading Apple stocks all day instead.

First, I wanna know how much money I could have made yesterday if I'd been trading Apple stocks all day.

So I grabbed Apple's stock prices from yesterday and put them in an array called stockPrices, where:

The indices are the time (in minutes) past trade opening time, which was 9:30am local time.
The values are the price (in US dollars) of one share of Apple stock at that time.
So if the stock cost $500 at 10:30am, that means stockPrices[60] = 500.

Write an efficient function that takes stockPrices and returns the best profit I could have made from one purchase and one sale of one share of Apple stock yesterday.

For example:

```
const stockPrices = [10, 7, 5, 8, 11, 9];

getMaxProfit(stockPrices);
// Returns 6 (buying for $5 and selling for $11)
```

No "shorting"—you need to buy before you can sell. Also, you can't buy and sell in the same time step—at least 1 minute has to pass.

# Thoughts

We need to check if there are at least two stock prices available for us to buy from. Therefore if there are less than two stock prices we return no profit since we cannot perform a buy and sell.

If we have a legitimate assortment. Then we can keep a high and low. We also keep a difference everytime we change our high and low and make sure that is maximized.

Time Complexity `O(n)`

- Where n is the array length
  Space Complexity `O(1)`
- We only need to keep track of some variables

# Code

```JS
const maxStock = stockArr => {
  // no profit, or throw error cause stock market invalid
  if (stockArr.length < 2) return 0;

  // initialize with the first buy possible
  let buyPrice = stockArr[0];
  let sellPrice = stockArr[1];
  let maxProfit = sellPrice - buyPrice;

  for (let i = 1; i < stockArr.length; i++) {
    const nowPrice = stockArr[i];

    if (nowPrice > sellPrice) {
      sellPrice = nowPrice;
    } else if (nowPrice < buyPrice) {
      buyPrice = nowPrice;
      i++
      sellPrice = stockArr[i];
    }

    const profit = sellPrice - buyPrice;
    if (profit > maxProfit) maxProfit = profit;
  }

  return maxProfit;
}
```
