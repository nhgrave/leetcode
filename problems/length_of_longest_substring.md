# Longest Substring Without Repeating Characters

O problema "Longest Substring Without Repeating Characters" consiste em verificar qual a maior sequencia de caracteres em sequencia sem repetir um caractere.

```javascript
function lengthOfLongestSubstring(string) {
  let collection = new Set();
  let count = 0;
  let max = 0;

  for (let i = 0; i < string.length; i++){
    while (collection.has(string[i])) {
      collection.delete(string[i - count]);
      count--;
    }

    collection.add(string[i]);
    count++;

    max = Math.max(max, count);
  }

  return max;
}

lengthOfLongestSubstring("abcabcbb"); // 3
lengthOfLongestSubstring("bbbbb"); // 1
lengthOfLongestSubstring("pwwkew"); // 3
lengthOfLongestSubstring("abcdbaef"); // 6
```
