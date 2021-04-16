<h2>Задание:<h2>
Создайте класс `RomanNumerals`, который может преобразовывать римскую цифру в целочисленное значение и обратно. Он должен следовать API, показанному в приведенных ниже примерах. Для каждого вспомогательного метода будет проверено несколько значений римских цифр.

Современные римские цифры пишутся путем выражения каждой цифры отдельно, начиная с самой левой цифры и пропуская любую цифру со значением нуля. В римских цифрах 1990 отображается: `1000=M`, `900=CM`, `90=XC`; в результате `MCMXC`. 2008 записывается как `2000=MM`, `8=VIII`; или `MMVIII`. `1666` использует каждый римский символ в порядке убывания: `MDCLXVI`.

<h2>Примеры:<h2>
	
```
RomanNumerals.to_roman(1000) # should return 'M'
RomanNumerals.from_roman('M') # should return 1000
```

<h2>Моё решение:<h2>

```
class RomanNumerals():

    # Разделение входного числа по римской системе
    def to_roman(n):
        ones = ["","I","II","III","IV","V","VI","VII","VIII","IX"]
        tens = ["","X","XX","XXX","XL","L","LX","LXX","LXXX","XC"]
        hunds = ["","C","CC","CCC","CD","D","DC","DCC","DCCC","CM"]
        thous = ["","M","MM","MMM","MMMM"]

        t = thous[n // 1000]
        h = hunds[n // 100 % 10]
        te = tens[n // 10 % 10]
        o =  ones[n % 10]

        return t+h+te+o

    # Буквы по римской системе в числа
    def from_roman(n):
        romanNumeralMap = (('M',  1000),
        ('CM', 900),('D',  500),
        ('CD', 400),('C',  100),('XC', 90),
        ('L',  50),('XL', 40),('X',  10),
        ('IX', 9),('V',  5),('IV', 4),('I',  1))

        result = 0
        index = 0

        # Сборка чисел по кортежу
        for numeral, integer in romanNumeralMap:
            while n[index:index+len(numeral)] == numeral:
                result += integer
                index += len(numeral)

        return result
```
