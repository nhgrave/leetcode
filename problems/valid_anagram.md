# Valid Anagram

O problema "Valid Anagram" consiste em analizar 2 strings e verificar se as duas tem os mesmos caracteres, exemplo: ovo e voo são anagramas.

```javascript
function validAnagram(string1, string2) {
  if (string1.length !== string2.length) return false;

  const count = {};
  for (const char of string1.toLowerCase()) {
    count[char] = (count[char] || 0) + 1;
  }

  for (const char of string2.toLowerCase()) {
    if (!count[char]) return false;
    count[char]--;
  }

  return true;
}

validAnagram("estudo", "duetos"); // true
validAnagram("Iracema", "America"); // true
validAnagram("aaa", "bbb"); // false
```
