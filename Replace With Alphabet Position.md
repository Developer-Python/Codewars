<h2>Задание:</h2>

В этом ката вы должны, получив строку, заменить каждую букву ее позицией в алфавите.

Если что-то в тексте не является письмом, игнорируйте его и не возвращайте.

`"а" = 1`, `"б" = 2` и `т. д`.

<h2>Примеры:</h2>

```

alphabet_position("The sunset sets at twelve o' clock.")
>>> "20 8 5 19 21 14 19 5 20 19 5 20 19 1 20 20 23 5 12 22 5 15 3 12 15 3 11"

```

<h2>Моё решение:</h2>

```
def alphabet_position(text):
    array = []
    # Меняе регистр на нижний
    text = text.lower()

    # Алфавит ASCll в нижнем регистре
    string_ascii_lower = 'abcdefghijklmnopqrstuvwxyz'

    # Фильтруем от мусора(к примеру: %^$#@*+1...9 )
    for i in text:
        if i in string_ascii_lower:
            array.append(i)

    # Склейваем отфильтрованный результат
    result = ' '.join(array)

    # Заменяем все буквы на позиций букв алфавита
    for pos, word in enumerate(string_ascii_lower, 1):
        result = result.replace(word,str(pos))

    # Возвращаем результат
    return result
```

<h6><span>Автор:</span> Орлов Евгений.</h6>
