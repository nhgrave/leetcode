# Rotate Array

O problema "Rotate Array" consiste em mover para a direita os elementos do array X vezes.


```javascript
function rotate(nums, k) {
  k = k % nums.length;

  reverse(nums, 0, nums.length - 1);
  reverse(nums, 0, k - 1);
  reverse(nums, k, nums.length - 1);

  function reverse(arr, start, end) {
    while (start < end) {
      [arr[start], arr[end]] = [arr[end], arr[start]];
      start++;
      end--;
    }
  }

  return nums;
}

rotate([1, 2, 3, 4, 5, 6, 7], 3); // [5, 6, 7, 1, 2, 3, 4]
```
