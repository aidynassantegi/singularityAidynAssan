# IOS Homeworks: Singularity 

## Первая неделя

## Вторая неделя

**Домашнее Задание:**

1. Напишите функцию, которая определяет четное число или нет.
```
func isEven(number: Int) -> Bool {
    number%2==0
}
```

2. Напишите функцию counts(arr: [Int], value: Int) -> Int, которая возвращает Int. Возвращаемое число должно быть количеством раз, которое value появляется в массиве. Например, counts(arr: [2, 1, 2, 2, 4, 4], value: 2) должно возвращать 3.
```
func counts(arr: [Int], value: Int) -> Int {
    var counter = 0
    for number in arr {
        if number == value {
            counter+=1
        }
    }
    return counter
}
```

3. Напишите функцию, которая по двум массивам вычисляет сумму попарных произведений. Например, sumOfProducts([3, 4, 5], [6, 7, 8]) должна возвращать 3 * 6 + 4 * 7 + 5 * 8 = 86. (Можно предположить, что оба массива будут иметь одинаковое количество элементов) .

```
func sumOfProducts(multipliers: [Int], multiplicands: [Int]) -> Int {
    guard multipliers.count == multiplicands.count else{return 0}
    var sum = 0
    for i in 0..<multipliers.count {
        sum += multipliers[i]*multiplicands[i]
    }
    return sum
}
```