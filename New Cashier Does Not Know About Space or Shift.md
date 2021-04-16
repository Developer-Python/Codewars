<h2>Задание:</h2>

В вашем ресторане начали работать новые кассиры.

Они хорошо выполняют приказы, но не умеют писать слова с большой буквы или использовать пробел!

Все заказы, которые они создают, выглядят примерно так:

`"milkshakepizzachickenfriescokeburgerpizzasandwichmilkshakepizza"`

Кухонный персонал грозится уволиться из-за того, как трудно читать приказы.

Они предпочитают получать заказы в виде красивой чистой строки с пробелами и заглавными буквами вот так:

`"Бургер Фри Курица Пицца Пицца Пицца Сэндвич Молочный Коктейль Молочный Коктейль Кока-кола"`

Кухонный персонал ожидает, что продукты будут в том же порядке, что и в меню.

Пункты меню довольно просты, в названиях пунктов нет перекрытия:

```
1. Burger
2. Fries
3. Chicken
4. Pizza
5. Sandwich
6. Onionrings
7. Milkshake
8. Coke

```

<h2>Примеры:</h2>

```
get_order("milkshakepizzachickenfriescokeburgerpizzasandwichmilkshakepizza")
>>> "Burger Fries Chicken Pizza Pizza Pizza Sandwich Milkshake Milkshake Coke")

get_order("pizzachickenfriesburgercokemilkshakefriessandwich")
>>> "Burger Fries Fries Chicken Pizza Sandwich Milkshake Coke")

```

<h2>Моё решение:</h2>

```
def get_order(order):
    # Так-как, мы знаем, что элементы статичны, тогда можно просто переписать в нижнем регистре -
    # - в иним случае, я бы циклом прошёлся по каждому элементу с методом .lower()
    menu_lower = ['burger','fries','chicken','pizza','sandwich','onionrings','milkshake','coke']
    new_order = []
    # Обходим каждый элемент(слово)
    for i in menu_lower:
        # Считаем кол-во вхождений
        count_word = order.count(i)
        # Дублируем строку столько раз сколько она повторяется
        i = i * count_word
        # Вырезаем первые 3 буквы дублированного слова
        start_word = i[0:3]
        # Заменяем 3 буквы, на точно такой же только с пробелом(слева)
        i = i.replace(start_word, ' '+start_word.capitalize())
        # Удаляем лишний пробел(слева)
        i = i.lstrip()
        new_order.append(i)

    # Соединяем список, и фильтруем от мусора(пустых значений)
    result = ' '.join(list(filter(None, new_order)))
    return result
```
<h6><span>Автор:</span> Орлов Евгений.</h6>
