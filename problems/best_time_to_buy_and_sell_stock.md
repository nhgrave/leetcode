# Best Time to Buy and Sell Stock

O problema "Best Time to Buy and Sell Stock" consiste em descobrir qual o melhor/maior lucro posivel ao comprar e vender uma ação. A ideia é encontrar a maior diferença entre 2 números N2 - N1 sendo que N2 deve estar depois de N1 no array. Esse problema simula variação dos preços de mercado a fim de prever lucro com base em históricos.

```javascript
const prices = [7, 2, 5, 3, 6, 2];

function maxProfit(prices = []) {
  let minPrice = Infinity;
  let maxProfit = 0;

  for (let i; i < prices.length; i++) {
    if (prices[i] < minPrice) {
      minPrice = prices[i];
    } else {
      const profit = price - minPrice;

      maxProfit = Math.max(profit, maxProfit);
    }
  }

  return maxProfit;
}

maxProfit(prices);
```
