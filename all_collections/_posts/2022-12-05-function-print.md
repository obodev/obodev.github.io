---
layout: post
title: Функция print()
date: 2022-12-05
categories: ["Swift", "SPL", "Function", "Debugging"]
---

# Функция print()

Функция **print()** записывает текстовые представления заданных элементов в стандартный вывод.

С помощью данной функции можно вывести в область отладки (иногда называемую консолью) заданную информацию в виде текстовой строки.

## Общий синтаксис функции print()

Эта функция встроенная в язык Swift и она объявлена так:

```swift
func print(
    _ items: Any...,
    separator: String = " ",
    terminator: String = "\n"
)
```

Функция принимает три параметра:

- items - Ноль или более элементов для печати;
- separator - Строка для печати между каждым элементом. По умолчанию используется один пробел (" ");
- terminator - Строка для печати после того, как все элементы будут напечатаны. По умолчанию используется новая строка ("\n").

## Использование функции print()

Функцию **print()** используют для проверки кода на ошибки. Можно передать в неё какой-нибудь элемент, чтоб проверить какое значение он содержит, отследить выполнение части кода и выполнение других функций. Например, отследить нажатие кнопки. Для этого достаточно в метод нажатия кнопки добавить вывод в консоль какого-то определенного текста.

В конечном проекте все вызовы функции `print()` удаляются, так как она необходима в основном для отладки приложения и отслеживания его работоспособности.

Можно передать ноль или более элементов функции `print(_:separator:terminator:)`. Текстовое представление для каждого элемента такое же, как и при вызове `String(item)`.

Например, рассмотрим следующий код:

```swift
print("Привет!")

// Output
// Привет!
```

Этот код выведет сообщение в консоль «Привет».

Достаточно часто в данной функции второй и третий параметры используются со значением по умолчанию. Поэтому они не указываются при вызове функции.

В следующем примере на стандартный вывод выводится строка, замкнутый диапазон целых чисел и группа значений с плавающей запятой:

```swift
print("One two three four five")

// Output
// One two three four five

print(1...5)

// Output
// 1...5

print(1.0, 2.0, 3.0, 4.0, 5.0)

// Output
// 1.0 2.0 3.0 4.0 5.0
```

Если передаются более одного элемента для вывода на печать, то элементы разделяются запятыми. Пример указан выше.

Чтобы напечатать элементы, разделенные чем-то другим, кроме пробела, следует передать разделитель как строку в параметр `separator`. Например:

```swift
print(1.0, 2.0, 3.0, 4.0, 5.0, separator: " ... ")

// Output
// 1.0 ... 2.0 ... 3.0 ... 4.0 ... 5.0
```

Вывод каждого вызова функции `print(_:separator:terminator:)` по умолчанию включает новую строку. Чтобы напечатать элементы без завершающей новой строки, следует передать пустую строку в качестве значения параметра `terminator`.

```swift
for n in 1...5 {
    print(n, terminator: "")
}

// Output
// 12345
```

В этом примере выполняется цикл и в каждой его итерации выполняется вызов функции `print()`. Но так как параметр `terminator` имеет в качестве значения пустую строку, то после каждого вывода элемента в консоль - курсор не будет переходить на новую строку и будет выводить последующий элемент в этой же строке. После выполнения цикла курсор по прежнему останется на этой строке. Для переноса курсора на новую строку можно вызвать функцию `print()` с пустыми параметрами.

Если необходимо вывести строковый элемент в несколько строчек, то можно использовать либо многостроковую строку либо добавлять оператор, который указывает на перенос курсора на новую строку - "\n".

Пример с многостроковой строкой:

```swift
print("""
some string one
some string two
""")

// Output
// some string one
// some string two
```

Пример с оператором "\n":

```swift
print("some string one\nsome string two")

// Output
// some string one
// some string two
```

В этом примере `\n` будет восприниматься как команда перехода на новую строку.

## Дополнительно

Для того, чтоб проверить результат выполнения функции с возвращаемым значением, можно передать в функцию `print()` вызов проверяемой функции:

```swift
func someFunc(a: Int, b: Int) -> Int {
    return a + b
}
print(someFunc(a: 2, b: 3))

// Output
// 5
```

Можно вывести в консоль тип данных элемента, передав в качестве элемента функцию *type(of:)*:

```swift
var str = "some string"
print(str, type(of: str))

// Output
// some string String

var array = [1, 2, 3]
print(array, type(of: array))

// Output
// [1, 2, 3] Array<Int>
```

---

## Еще полезные ссылки

- [Переменные и константы](https://robot.obo.dev/read/posts/variable/)
- [Операторы](https://robot.obo.dev/read/posts/operator/)
- [Типы данных](https://robot.obo.dev/read/posts/data-type/)
- [Опционалы](https://robot.obo.dev/read/posts/optional-data-type/)
- [Кортежи](https://robot.obo.dev/read/posts/tuple/)
- [Функции](https://robot.obo.dev/read/posts/function/)

Ссылки на официальную документацию:

- [Apple Developer Documentation - Print()](https://developer.apple.com/documentation/swift/print(_:separator:terminator:))