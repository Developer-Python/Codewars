<h1>Task:</h1>
Create a simple calculator that given a string of operators (), +, -, *, / and numbers separated by spaces returns the value of that expression.
You can not use eval, exec, kata goal that you would write a valid calculator yourself.
<h2>Example:</h2>

`Calculator().evaluate("2 / 2 + 3 * 4 - 6") # => 7`
Remember about the order of operations! Multiplications and divisions have a higher priority and should be performed left-to-right. Additions and subtractions have a lower priority and should also be performed left-to-right.

<hr>

<h2>Tests:</h2>

```
"2 + 3" == 5
"2 + 3" == 5
"2 - 3 - 4" == -5
"10 * 5 / 2" == 25
"2 / 2 + 3 * 4 - 6" == 7
"2 + 3 * 4 / 3 - 6 / 3 * 3 + 8" == 8
"1.1 + 2.2 + 3.3" == 6.6
"1.1 * 2.2 * 3.3" == 7.986
```

<hr>

<h2>My Solution</h2>

```
class Calculator(object):
  def evaluate(self, string):
  
    # Deleting all spaces(compressing).
    s = ''.join(string.split())
    
    # Creating a list generator, where we put spaces between operators, and translate all numbers to float.
    result = [float(operation) if operation not in '/*-+' else operation for operation in s.replace('+', ' + ').replace('-', ' - ').replace('*', ' * ').replace('/', ' / ').split()]
    
    # If the operator (+ -*/) occurs, then we add the result of the fulfilled operator functions to the array.
    for c in '/*-+':
        array = []
        for decide in result:
            if array and array[-1] == c:
                array.pop()
                decide = {'/':lambda a,b: a/b, '*':lambda a,b: a*b, '-':lambda a,b: a-b, '+':lambda a,b: a+b}[c](array.pop(), decide)
            array.append(decide)
                
        result = array
        
    # Returning the result without the last element.
    return result.pop()
```
