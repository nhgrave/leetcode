# Merge Intervals

O problema "Merge Intervals" consiste em unificar intervalos de valores que se sobrepoem, juntando eles e retornando um intervalo maior. Dado um array de intervalos `intervals` onde cada intervalo é representado por um par `[start, end]`, una todos os intervalos sobrepostos e retorne um novo array com os intervalos mesclados. Esse problema pode simula sobreposição de agendamentos.

```javascript
function mergeIntervals(intervals = []) {
  intervals.sort((a, b) => a[0] - b[0]);

  const merged = [intervals[0]]

  let lastMergedIndex = 0;

  for (let index = 1; index < intervals.length; index++) {
    const lastMerged = merged[lastMergedIndex];
    const current = intervals[index];

    if (current[0] <= lastMerged[1]) {
      lastMerged[1] = Math.max(lastMerged[1], current[1])
    } else {
      merged.push(current)
      lastMergedIndex++;
    }
  }

  return merged;
}

mergeIntervals([[1, 3], [2, 6], [8, 10], [15, 18]]); // [[1, 6], [8, 10], [15, 18]]
/*
1-2-3
  2-3-4-5-6
              8-9-10
                                 15-16-17-18
--------------------------------------------
1-2-3-4-5-6   8-9-10             15-16-17-18
*/

mergeIntervals([[1, 3], [5, 8], [2, 6], [15, 18], [8, 10]]); // [[1, 10], [15, 18]]
/*
1-2-3
  2-3-4-5-6
        5-6-7-8
              8-9-10
                                 15-16-17-18
--------------------------------------------
1-2-3-4-5-6-7-8-9-10             15-16-17-18
*/
```
