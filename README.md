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

2. Напишите функцию `counts(arr: [Int], value: Int) -> Int`, которая возвращает `Int`. Возвращаемое число должно быть количеством раз, которое value появляется в массиве. Например, `counts(arr: [2, 1, 2, 2, 4, 4], value: 2)` должно возвращать 3.
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

3. Напишите функцию, которая по двум массивам вычисляет сумму попарных произведений. Например, `sumOfProducts([3, 4, 5], [6, 7, 8])` должна возвращать `3 * 6 + 4 * 7 + 5 * 8 = 86`. (Можно предположить, что оба массива будут иметь одинаковое количество элементов) .

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

```
enum ShapeType {
    case circle(Double)
    case rectangle(Double, Double)
}

func calculateArea(shape: ShapeType) -> Double {
    switch shape {
    case .circle(let radius): return 3.14*radius*radius
    case .rectangle(let height, let length): return height*length
    }
}

let recArea = calculateArea(shape: .rectangle(12, 12))
let circleArea = calculateArea(shape: .circle(1))
print(recArea)
print(circleArea)

```

3. Создать `enum` с названием `ResultType`
* Создать 2 случая, `success/failure`
* Добавить связанное значение типа `(Int)` для случая `success`
* Добавить связанное значение типа `(String)` для случая `error`
Создать функцию с названием getGrade
Добавить туда аргумент completion с типом (ResultType) -> Void (это closure)
Внутри функции создать переменную isSuccess типа Bool, которая случайно будет выбирать между true и false(google it).
* Далее если `isSuccess == true`  , нужно вызвать функцию, которая является аргументом `getGrade` , передав туда `ResultType.success` со значением 95
* Если `isSuccess == false`, нужно также вызвать функцию которая является аргументом `getGrade`, передав туда `ResultType.failure` со значением `"Grades not available yet, try again later"`

```
enum ResultType {
    case success(Int)
    case failure(String)
}

func getGrade(completion: (ResultType)->Void) {
    let isSuccess: Bool = Bool.random()
    if isSuccess {
        completion(.success(95))
    }else {
        completion(.failure("Grades not available yet, try again later"))
    }
}
```

**6.2 Пользовательские типы данных, их свойства и методы**

**Задания на Structs & Classes**

1. Создать класс `Circle`, добавить свойство radius типа `Double`. Далее нужно написать функцию `calculateArea`, которая будет принимать параметр типа `Circle` и возвращать площадь, топ которого будет `Double`
```
class Circle {
    let radius: Double
    init(radius: Double) {
        self.radius = radius
    }
}

func circleArea(circle: Circle) -> Double {
    circle.radius * circle.radius * 3.14
}

let myCircle = Circle(radius: 10)
print(circleArea(circle: myCircle))
```
2. Создать класс `Rectangle`, добавить свойства `length` и `width` типа `Double`. Далее нужно написать функцию `calculateArea`, которая будет принимать параметр типа `Rectangle` и возвращать площадь, топ которого будет `Double`

```
class Rectangle {
    let length: Double
    let width: Double
    init(length: Double, width: Double) {
        self.length = length
        self.width = width
    }
}

let myRect = Rectangle(length: 10, width: 5)
func rectArea(of rect: Rectangle) -> Double {
    rect.length*rect.width
}

print(rectArea(of: myRect))

```
**6.2 Пользовательские типы данных, их свойства и методы**

Реализуйте классическую детскую игру «Камень-ножницы-бумага».

«Камень, ножницы, бумага» — игра для двух игроков. Каждый игрок выбирает камень, ножницы или бумагу, не зная выбора другого игрока.

Победитель определяется по ряду правил:

Камень побеждает ножницы
Ножницы бьют бумагу
Бумага побеждает камень
Если оба игрока выбирают одно и то же, в этом раунде нет победителя.

*** Добавить дополнительные оружия - [Ссылка](https://en.wikipedia.org/wiki/Rock_paper_scissors#Additional_weapons)

```
/Для отладки используйте Xcode или online компиллятор http://online.swiftplayground.run
//Результат выведите в print


let input = readLine()!.split(separator: " ")        //rock scissors - Считываем проверочные параметры
let first = String(input.first!)                            //rock - 1 параметр в поле ввода - String
let second = String(input.last!)                            //scissors - 2 параметр в поле ввода - String

// 1. Определить тип для rock, paper, scissors и назвать его Choice. Какой подойдет лучше?

enum Choice {
    case rock
    case scissors
    case paper
}

// 2. Создать computed property для типа Choice, чтобы вычислять weakness

var weakness: Choice? {
    switch (first, second) {
    case ("rock" , "scissors"): return .scissors
    case ("rock" , "paper"): return .rock
    case ("paper" , "scissors"): return .paper
    case ("paper", "rock"): return .paper
    case ("scissors", "rock"): return .scissors
    case ("scissors", "paper"): return .paper
    default: return nil
    }
}

// 3. Создать структуру Game
//    a. Создать свойства для хранения счета двух игроков(p1Score, p2Score)
//    b. Создать свойство для хранения истории прошлых игр
//    c. Создать метод play внутри которого будут передаваться выборы игроков
//        i. Обновлять историю игр
//        ii. В зависимости от победителся повышать p1Score/p2Score и принтить "player 1 wins" / "player 2 wins" / "draw"
struct Game {
    var p1Score = 0
    var p2Score = 0
    var prevGames: [[Choice]] = []
    
    mutating func(p1Choice)
    
}
// 4. инициализировать выборы игроков используя first & second. Hint: rawValue


//game.play(p1Choice, against: p2Choice)

```