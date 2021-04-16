<h1>Задание:</h1>
Создайте простой калькулятор, который задал строку операторов (), +, -, *, / а числа, разделенные пробелами, возвращают значение этого выражения.
Вы не можете использовать eval, exec, kata goal, чтобы вы сами написали действительный калькулятор.
<h2>Пример:</h2>

`Calculator().evaluate("2 / 2 + 3 * 4 - 6") # => 7`
Помните о порядке действий! Умножение и деление имеют более высокий приоритет и должны выполняться слева направо. Сложение и вычитание имеют более низкий приоритет и также должны выполняться слева направо.

<hr>

<h2>Тесты:</h2>

```
Calculator().evaluate("2 + 3") => 5
Calculator().evaluate("2 + 3)" => 5
Calculator().evaluate("2 - 3 - 4") => -5
Calculator().evaluate("10 * 5 / 2") => 25
Calculator().evaluate("2 / 2 + 3 * 4 - 6") => 7
Calculator().evaluate("2 + 3 * 4 / 3 - 6 / 3 * 3 + 8") => 8
Calculator().evaluate("1.1 + 2.2 + 3.3") => 6.6
Calculator().evaluate("1.1 * 2.2 * 3.3") => 7.986
```

<hr>

<h2>Моё решение</h2>
    
```
class Calculator(object):
  def evaluate(self, string):
  
    # Удаление всех пробелов(сжатие).
    s = ''.join(string.split())
    
    # Создание генератора списков, где мы ставим пробелы между операторами и переводим все числа в float.
    result = [float(operation) if operation not in '/*-+' else operation for operation in s.replace('+', ' + ').replace('-', ' - ').replace('*', ' * ').replace('/', ' / ').split()]
    
    # Если встречается оператор ( + - * / ), то мы добавляем в массив результат выполненных операторных функций.
    for c in '/*-+':
        array = []
        for decide in result:
            if array and array[-1] == c:
                array.pop()
                decide = {'/':lambda a,b: a/b, '*':lambda a,b: a*b, '-':lambda a,b: a-b, '+':lambda a,b: a+b}[c](array.pop(), decide)
            array.append(decide)
                
        result = array
        
    # Возврат результата без последнего элемента.
    return result.pop()
```
<h6><span>Автор:</span> Орлов Евгений.</h6>
