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
# Инструменты для итераций
import itertools


def permutations(string):
    array = []
    
    # Добовляем в инструмент "строку" и "длинну этой строки"
    permutations = list( itertools.permutations(string, r=len(string)))
    
    # Превращаем всё в список
    list_permutations = list(map(list, permutations))
    
    # Конвертируем в строку и добовляем в массив
    for i in list_permutations:
        array.append(''.join(i))
        
    # Конвертируем в список уже без повторения
    return list(set(array))
```

<h6><span>Автор:</span> Орлов Евгений.</h6>
