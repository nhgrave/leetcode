# Two Sum

O problema "Two Sum" consiste em encontrar dois números dentro de um array que, quando somados, resultam em um valor alvo específico e retornar os 2 indices do array em que os valores resultam no alvo. Esse problema de "Two Sum" pode ser encontrado em um problema de logística a fim de combinar pacotes com pesos que juntos atingem um limite de carga.

## Quando o array está ordenado

Quando o array estiver ordenado de forma crescente pode ser utilizado o método de "Two Pointers" onde temos um ponteiro no inicio (P1) e outro no final (P2), ambos andando em direção há se encontrar. Quando verificar a soma dos valores, caso a soma for menor que o alvo o ponteito P1 se meve, caso a soma for maior que o alvo o P2 se move, até encontrar o valor ou ambos chegarem ao mesmo indice. Esse método tem performance O(n) percorrendo apenas 1 ver cada item do array no pior dos casos.

```javascript
const array = [2, 3, 5, 7, 11, 13, 17];
const target = 12;

function twoSum(numbers = [], target = 0) {
  let i = 0
  let j = numbers.length - 1;

  while (i < j) {
    const result = numbers[i] + numbers[j];

    if (result === target) {
      return [i, j];
    } else if (result < target) {
      i++;
    } else {
      j--;
    }
  }

  return [];
}

twoSum(array, target);
```

## Quando o array não estiver ordenado

Quando o array não estiver ordenado não podemos utilizar o método "Two Pointers", então usamos o método "Hash Map" salvando cada número do aray como a chave em um dicionario e o indice no valor da chave. Para verificar se se oncontrou os indices você deve subtrair do alvo o valor atual observado e com isso obter um valor faltante a ser encontrado no dicionario. Esse método tem performance O(n) percorrendo apenas 1 ver cada item do array no pior dos casos.

```javascript
const array = [2, 3, 5, 7, 11, 13, 17];
const target = 12;

function twoSum(numbers = [], target = 0) {
  const map = {};
  let result = [];

  for (let i = 0; i < numbers.length; i++) {
    const complement = target - numbers[i];

    if (map[complement] !== undefined) {
      result = [map[complement], i];
      i = numbers.length;
    } else {
      map[numbers[i]] = i;
    }
  }

  return result;
}

twoSum(array, target);
```
