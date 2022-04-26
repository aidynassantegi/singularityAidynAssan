# IOS Homeworks: Singularity 

## Первая неделя

## Вторая неделя

**6.1 Функции и Замыкания**

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

**6.2 Пользовательские типы данных, их свойства и методы**

**Задания на перечисления**

1. Создать enum с  названием `TransportType`. 
* Создать 3 случая - `airplane/train/car`.
* Создать функцию для определения вебсайта, которая будет принимать в качестве аргумента `TransportType` и возвращать тип `String`
* В функции в зависимости от значения аргумента, возвращать `www.airastana.com/www.bilet.railways.kz/www.indriver.com`


```
enum TransportType {
    case airplane
    case train
    case car
}

func ticketSite(of transport: TransportType) -> String {
    switch transport {
    case .airplane: return "www.airastana.com"
    case .train: return "www.bilet.railways.kz"
    case .car: return "www.indriver.com"
    }
}

let myTransport: TransportType = .airplane
print(ticketSite(of: myTransport))

```

2. Создать `enum` с названием `ShapeType`.
* Создать 2 случая, `circle/rectangle`
* Добавить связанные значения(associated value) на каждый случай, чтобы высчитать площадь фигуры.
* Создать функцию `calculateArea`,  которая будет принимать тип `ShapeType` в качестве аргумента и возвращать тип `Double`.
* В функции в зависимости от связанных значений, высчитывать площадь по-разному.

3. Создать `enum` с названием `ResultType`
* Создать 2 случая, `success/failure`
* Добавить связанное значение типа `(Int)` для случая `success`
* Добавить связанное значение типа `(String)` для случая `error`
Создать функцию с названием getGrade
Добавить туда аргумент completion с типом (ResultType) -> Void (это closure)
Внутри функции создать переменную isSuccess типа Bool, которая случайно будет выбирать между true и false(google it).
* Далее если `isSuccess == true`  , нужно вызвать функцию, которая является аргументом `getGrade` , передав туда `ResultType.success` со значением 95
* Если `isSuccess == false`, нужно также вызвать функцию которая является аргументом `getGrade`, передав туда `ResultType.failure` со значением `"Grades not available yet, try again later"`