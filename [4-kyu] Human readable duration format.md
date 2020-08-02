Your task in order to complete this Kata is to write a function which formats a duration, given as a number of seconds, in a human-friendly way.

The function must accept a non-negative integer. If it is zero, it just returns "now". Otherwise, the duration is expressed as a combination of `years`, `days`, `hours`, `minutes` and `seconds`.

It is much easier to understand with an example:
```
format_duration(62)    # returns "1 minute and 2 seconds"
format_duration(3662)  # returns "1 hour, 1 minute and 2 seconds"
```
For the purpose of this Kata, a year is 365 days and a day is 24 hours.

Note that spaces are important.

Detailed rules
The resulting expression is made of components like `4 seconds`, `1 year`, etc. In general, a positive integer and one of the valid units of time, separated by a space. The unit of time is used in plural if the integer is greater than 1.

The components are separated by a comma and a space (`", "`). Except the last component, which is separated by `" and "`, just like it would be written in English.

A more significant units of time will occur before than a least significant one. Therefore, `1 second and 1 year` is not correct, but `1 year and 1 second` is.

Different components have different unit of times. So there is not repeated units like in `5 seconds and 1 second`.

A component will not appear at all if its value happens to be zero. Hence, `1 minute and 0 seconds` is not valid, but it should be just `1 minute`.

A unit of time must be used "as much as possible". It means that the function should not return 61 seconds, but 1 minute and 1 second instead. Formally, the duration specified by of a component must not be greater than any valid more significant unit of time.
<hr>

<h2>Tests:<h2>

```
format_duration(1) => "1 second",
format_duration(62) => "1 minute and 2 seconds",
format_duration(120) => "2 minutes",
format_duration(3600) => "1 hour",
format_duration(3662) => "1 hour, 1 minute and 2 seconds",
format_duration(9999) => "2 hours, 46 minutes and 39 seconds",
format_duration(1234567) => "14 days, 6 hours, 56 minutes and 7 seconds",
format_duration(300000022) => "9 years, 187 days, 5 hours, 20 minutes and 22 seconds"
```

<hr>

<h2>My Solution</h2>

```

def format_duration(seconds):

    array = []
    
    # Dividing the specified number of seconds.
    y = seconds // 31536000
    d = seconds // 86400 % 365
    h = seconds // 3600 % 24
    m = seconds // 60 % 60
    s = seconds % 60
    
    
    # We glue the resulting number with the desired unit of time measurement,
    # if the number is equal to 1, then we do not touch the ending,
    # but if the number is more than one, we add 's'.
    
    if y == 0:
        pass
    elif y == 1:
        array.append(str(y) +' year')
    elif y >= 2:
        array.append(str(y) +' years')
        
    # We glue the resulting number with the desired unit of time measurement.
    if d == 0:
        pass
    elif d == 1:
        array.append(str(d) +' day')
    elif d >= 2:
        array.append(str(d) +' days')
        
    # We glue the resulting number with the desired unit of time measurement.
    if h == 0:
        pass
    elif h == 1:
        array.append(str(h) +' hour')
    elif h >= 2:
        array.append(str(h) +' hours')
        
    # We glue the resulting number with the desired unit of time measurement. 
    if m == 0:
        pass
    elif m == 1:
        array.append(str(m) +' minute')
    elif m >= 2:
        array.append(str(m) +' minutes')
        
    # We glue the resulting number with the desired unit of time measurement.
    if s == 0:
        pass
    elif s == 1:
        array.append(str(s) +' second')
    elif s >= 2:
        array.append(str(s) +' seconds')
    
    
    # If the array is empty, it means the time is now!
    if array == []:
        return 'now'
    
    # Get len this array.
    len_array = len(array)
    
    # Gluing together enumerations, if they have.
    if len_array >= 2:
        if len_array == 2:
            result = ''.join(array[:-2])+ '' + ' and '.join(array[len_array - 2:len_array])
        else:
            result = ', '.join(array[:-2])+ ', ' + ' and '.join(array[len_array - 2:len_array])
    else:
        result = ' '.join(array)
    
    return result
```

<h6><span>Author:</span> Orlov Evgenu.</h6>
