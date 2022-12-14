---
layout: post
title: Немного про циклы
date: 2022-08-08
categories: ["Swift", "SPL" , "Циклы"]
---

# Что такое цикл?

Цикл, очевидно, это инструмент, который позволяет делать повторяющиеся действия. Тебе, чтобы побороть цикл, придётся применить чуток внимательности и усилий.

> Ты так же можешь встретить определение - **оператор управления потоком**

На данный момент науке известны три вида циклов в яп **Swift**.

## While
> Дословно звучит как "ПОКА", "ПОКУДА", "ДОКОЛЕ" -> "ДЕЛАЙ ЧТО-ТО"


Это походу самый простой цикл, который можно себе представить, выглядит примерно так:

```swift

while УСЛОВИЕ {
  КОДЕЦ, КОТОРЫЙ НАДО ВЫПОЛНИТЬ
}

```

Условие всегда принимает `Bool`. Это может быть результат работы функции или оператора, не важно, главное, чтобы там всегда был `Bool`. Пихнёшь туда `Bool` и все будет работать как надо. Например, можно даже попробовать дотянуться до бесконечности:

```swift

while true {
  print("to the infinity and beyond")
}

```

> Подобные устремления крайне сильно одобряется этим персонажем - 
> ![Buzz Lightyear](https://github.com/obodev/obodev.github.io/blob/main/assets/images/buzz-lightyear.gif?raw=true)

```swift

var iterator: Int = 1
var sum: Int = 0

while iterator < 10 {
  sum += i 
  i += 1
}
//Код, аналогичный подобному выражению: 1+2+3+4+5+6+7+8+9

print(sum) //печатает 45

```

Примеры выше наглядно показывают пользу.

## Repeat – While
> Дословно звучит как "ДЕЛАЙ ЧТО-ТО" -> "ПОКА", "ПОКУДА", "ДОКОЛЕ"

Из дословного перевода становится понятно, что он работает так же как и `while`, но чутка наоборот:

```swift

var i: Int = 1
var runLoop: Bool = false
var sum: Int = 0

while runLoop {
  sum += i
  i += 1
}

print(sum) //печатает 0

```

> Делает он так по очевидной причине, в условие передан `false` и цикл отрабатывает **0 раз**


**НО**, попробуем сделать то же самое с применением `repeat - while`:

```swift
  
var i: Int = 1
var runLoop: Bool = false
var sum: Int = 0
  
repeat {
  sum += i
  i += 1
} while runLoop

print(sum) //печатает 1

```

И сразу же видим, что результат отличается. Отличие связано с тем, что в отличие от `while`, `repeat - while` сначала выполняет действие, а потом проверяет условие. Поэтому, он всегда отрабатывает хотя бы один раз.

# For – In
> Дословно звучит как "ДЛЯ КАЖДОГО ЧЕГО-ТО В ЧЕМ-ТО"

Один из самых популярных инструментов. Ты будешь им пользоваться каждый день.

Выглядит так:

```swift
  
for ЧТО-ТО in ЧЕМ-ТО {
  КОДЕЦ, КОТОРЫЙ НАДО ВЫПОЛНИТЬ
  ЧТО-ТО доступно внутри его области видимости
}
  
```

Например, мы решили сложить все числа в последовательности `0...9`:

```swift
  
var sum: Int = 0
  
for i in 1...9 {
  sum += i
}
  
print(sum) //печатает 45


```

Получается, что для каждого `i` в последовательности `0...9` к `sum` будет прибавляться `i`. Он начнёт с 0 и будет перебирать все числа в последовательности, пока последовательность не закончится.

Таким образом, можно перебирать любую последовательность, например массив:

```swift
  
let dudes = ["Миша", "Гриша", "Толя", "Опанас", "Ваня"]
  
for dude in dudes {
  print("Привет, \(dude)!")
}
  
// Привет, Миша!
// Привет, Гриша!
// Привет, Толя!
// Привет, Опанас!
// Привет, Ваня!
  
```

> Важно помнить, что название итератору мы даём сами, это сделано для нашего же удобства. В первом примере мы назвали итератор `i` и использовали это имя внутри цикла, во втором же это был `dude`.

Это всё, теперь ты знаешь как использовать циклы! 🙂