<h2>Задание:</h2>
В этом ката вы должны создать все перестановки входной строки и удалить дубликаты, если таковые имеются. Это означает, что вы должны перетасовать все буквы из ввода во всех возможных порядках.

<h2>Примеры:</h2>

```
permutations('a'); # ['a']
permutations('ab'); # ['ab', 'ba']
permutations('aabb'); # ['aabb', 'abab', 'abba', 'baab', 'baba', 'bbaa']
```

Порядок перестановок не имеет значения.

<h2>Моё решение:</h2>

```
import itertools

def permutations(string):
    array = []

    permutations = list( itertools.permutations(string, r=len(string)))
    list_permutations = list(map(list, permutations))

    for i in list_permutations:
        array.append(''.join(i))

    return list(set(array))
```

<h6><span>Автор:</span> Орлов Евгений.</h6>
