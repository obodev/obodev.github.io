---
layout: post
title: Приоритет операторов и ассоциативность (Operator precedence and associativity)
date: 2022-12-28
categories: ["Swift", "SPL"]
---

# Приоритет операторов и ассоциативность

Если бы мы разобрали выражение — скажем, `1 + 2` — и разложили его на составные части, то нашли бы один оператор и два операнда:

Левый операнд | Оператор | Правый операнд
:------------:|:--------:|:--------------:
1             | +        | 2

Выражения выражены в одной плоской строке кода, из которой компилятор строит абстрактное синтаксическое дерево (abstract syntax tree, AST):

![](https://obodev.github.io/assets/images/operator-precedence-ast-0.png)

Возьмем пример, предположим, что в выражении более одного оператора.

```
var num = 8 + 5 * 4 // 28
```

Здесь, 

- если `+` выполняется первым, значение num будет равно `52`;
- если `*` выполняется первым, значение num будет равно `28`.

Для составных выражений, таких как `1 + 2 * 3` или `5 - 2 + 3`, компилятор использует правила приоритета операторов и ассоциативности, чтобы преобразовать выражение в одно значение.

## Приоритет операторов

Приоритет операторов — это набор правил, определяющих, какой оператор выполняется первым. 

Прежде чем вы узнаете о приоритете операторов, обязательно узнайте об операторах Swift. См. ссылку внизу.

Правила приоритета операторов, аналогичные тем, которые вы изучали в начальной школе, определяют порядок, в котором оцениваются различные виды операторов. В этом случае умножение имеет более высокий приоритет, чем сложение, поэтому сначала вычисляется `2 * 3`.

Левый операнд | Оператор | Правый операнд
:------------:|:--------:|:--------------:
1             | +        | (2 * 3)

![](https://obodev.github.io/assets/images/operator-precedence-ast-1.png)

## Ассоциативность операторов

Ассоциативность определяет порядок, в котором разрешаются операторы с одинаковым приоритетом.

Если в выражении есть два оператора с одинаковым приоритетом, выражение оценивается в соответствии с его ассоциативностью (слева направо или справа налево). Например,

```
print(6 * 4 / 3)

// Output
// 8
```

Здесь операторы `*` и `/` имеют одинаковый приоритет. И их ассоциативность **слева направо**. Следовательно, `6 * 4` выполняется первым.

> Примечание. Если необходимо сначала выполнить деление, можно использовать круглые скобки для группирования. Например `print(6 * (4/3))`.

Ассоциативность бывает:

- Левая ассоциативность (Left Associativity) — операторы вычисляются слева направо.
- Правая ассоциативность (Right Associativity) — операторы вычисляются справа налево.
- Неассоциативность (Non-associativity) - операторы не имеют определенного поведения.

Если оператор левоассоциативен, то сначала вычисляется операнд в левой части: `((5 - 2) + 3)`; если правоассоциативный, то сначала вычисляется правый оператор: `5 - (2 + 3)`.

Арифметические операторы левоассоциативны, поэтому `5 - 2 + 3` имеет значение как `6`.

Левый операнд | Оператор | Правый операнд
:------------:|:--------:|:--------------:
(5 - 2)       | +        | 3

![](https://obodev.github.io/assets/images/operator-precedence-ast-2.png)

Ещё пример: приоритет оператора со сложным оператором присваивания

```
var num = 15

num += 10 - 2 * 3
print(num)

// Output
//19
```

В приведенном выше примере создали переменную `num` со значением `15`. Обратите внимание на выражение `num += 10 - 2 * 3`.

Здесь порядок приоритета от высшего к низшему равен `*`, `-` и `+=`. Следовательно, выражение выполняется как `num += 10 - (2 * 3)`.

## Операторы Swift

Стандартная библиотека Swift включает в себя большинство операторов, которые программист может ожидать найти от другого языка семейства C, а также несколько удобных дополнений, таких как оператор nil-coalescing (`??`) и оператор сопоставления с образцом (`~=`), а также операторы для проверки типов (`is`), приведения типов (`as`, `as?`, `as!`) и формирования открытые или закрытые диапазоны (`...`, `..<`).

## Инфиксные операторы (Infix Operators)

Инфиксные операторы сгруппированы ниже в соответствии с их ассоциативностью и уровнем приоритета в порядке убывания:

Группа **BitwiseShiftPrecedence**, которая не является ассоциативной, содержит следующие инфиксные операторы:

Оператор | Описание
:-------:|:--------------
`<<`     | Побитовый сдвиг влево
`>>`     | Побитовый сдвиг вправо
`&<<`    | Побитовый сдвиг влево, игнорируя переполнение
`&>>`    | Побитовый сдвиг вправо, игнорируя переполнение

Группа **MultiplicationPrecedence**, ассоциативная слева, содержит следующие инфиксные операторы:

Оператор | Описание
:-------:|:--------------
`*`      | Умножение
`/`      | Деление
`%`      | Остаток от деления
`&`      | Побитовое И (Bitwise AND)
`&*`     | Умножение с переполнением (Умножить, игнорируя переполнение)
`&/`     | Деление с переполнением (Делить, игнорируя переполнение)
`&%`     | Остаток от деления с переполнением (Остаток от деления, игнорируя переполнение)

Группа **AdditionPrecedence**, ассоциативная слева, содержит следующие инфиксные операторы:

Оператор | Описание
:-------:|:--------------
`+`      | Сложение
`-`      | Вычитание
`\|`     | Побитовое ИЛИ (Bitwise OR)
`^`      | Побитовое исключающее ИЛИ (Bitwise XOR)
`&+`     | Сложение с переполнением (Добавить, игнорируя переполнение)
`&-`     | Вычитание с переполнением (Вычесть, игнорируя переполнение)

Группа **RangeFormationPrecedence**, которая не является ассоциативной, содержит следующие инфиксные операторы:

Оператор | Описание
:-------:|:--------------
`..<`    | Полуоткрытый диапазон
`...`    | Закрытый диапазон

Группа **CastingPrecedence**, ассоциативная слева, содержит следующие инфиксные операторы:

Оператор | Описание
:-------:|:--------------
`is`     | Проверка типа
`as`, `as?`, `as!`    | Приведение типа

Группа **NilCoalescingPrecedence**, являющаяся правоассоциативной, содержит следующие инфиксные операторы:

Оператор | Описание
:-------:|:--------------
`??`     | Nil coalescing

Группа **ComparisonPrecedence**, которая не является ассоциативной, содержит следующие инфиксные операторы:

Оператор | Описание
:-------:|:--------------
`<`      | Меньше
`<=`     | Меньше или равно
`>`      | Больше
`>=`     | Больше или равно
`==`     | Равно
`!=`     | Не равно
`===`    | Идентично, тождественно
`!==`    | Не идентично, не тождественно
`~=`     | Соответствие шаблону
`.<`     | Поточечно меньше
`.<=`    | Поточечно меньше или равно
`.>`     | Поточечно больше
`.>=`    | Поточечно больше или равно
`.==`    | Поточечно равно
`.!=`    | Поточечно не равно

Группа **LogicalConjunctionPrecedence**, которая является левой ассоциативной, содержит следующие инфиксные операторы:

Оператор | Описание
:-------:|:--------------
`&&`     | Логическое И (Logical AND)
`.&`     | Поточечное побитовое И (Pointwise bitwise AND)

Группа **LogicalDisjunctionPrecedence**, которая является левой ассоциативной, содержит следующие инфиксные операторы:

Оператор | Описание
:-------:|:--------------
`\|\|`   | Логическое ИЛИ (Logical OR)
`.\|`    | Поточечное побитовое ИЛИ (Pointwise bitwise OR)
`.^`     | Поточечное побитовое исключающее ИЛИ (Pointwise bitwise XOR)

Группа **DefaultPrecedence**, которая не является ассоциативной. Если объявляете новый оператор без указания группы приоритета, он становится членом группы приоритета DefaultPrecedence.

Группа **TernaryPrecedence**, являющаяся правоассоциативной, содержит следующие инфиксные операторы:

Оператор | Описание
:-------:|:--------------
`?  :`     | Тернарный условный оператор

Группа **AssignmentPrecedence**, которая является правоассоциативной, содержит следующие инфиксные операторы:

Оператор | Описание
:-------:|:--------------
`=`      | Присваивать, назначить
`*=`     | Умножить и присвоить
`/=`     | Разделить и присвоить
`%=`     | Остаток от деления и присвоить
`+=`     | Добавить и присвоить
`-=`     | Вычесть и присвоить
`<<=`    | Левый битовый сдвиг и присвоить
`>>=`    | Правый битовый сдвиг и присвоить
`&=`     | Побитовое И и присвоить
`\|=`    | Побитовое ИЛИ и присвоить
`^=`     | Побитовое исключающее ИЛИ и присвоить
`&*=`    | Умножить с переполнением и присвоить
`&+=`    | Добавить с переполнением и присвоить
`&-=`    | Вычесть с переполнением и присвоить
`&<<=`   | Побитовый сдвиг влево с переполнением и присвоить
`&>>=`   | Побитовый сдвиг вправо с переполнением и присвоить
`.&=`    | Поточечное побитовое И и присвоить
`.\|=`   | Поточечное побитовое ИЛИ и присвоить
`.^=`    | Поточечное побитовое исключающее ИЛИ и присвоить

В таблице ниже сгруппирована информация, которая указана выше по приоритетам и ассоциативности операторов Swift. Чем выше находится оператор в таблице, тем выше его приоритет.

Оператор           | Группа                       | Пример      | Ассоциативность
:------------------|:-----------------------------|:-----------:|:---
Побитовый сдвиг    | BitwiseShiftPrecedence       | `>>` `<<`   | нет (none)
Мультиплицирование | MultiplicationPrecedence     | `*` `/` `%` | левая (left)
Добавление         | AdditionPrecedence           | `\|` `&` `^` `+` `-` | левая (left)
Диапазон           | RangeFormationPrecedence     | `..<` `...` | нет (none)
Приведение типа    | CastingPrecedence            | `is` `as`   | нет (none)
Nil-Coalescing     | NilCoalescingPrecedence      | `??`        | правая (right)
Сравнение          | ComparisonPrecedence         | `==` `===` `!=` `>` `<` `>=` `<=` | нет (none)
Логическое И       | LogicalConjunctionPrecedence | `&&`        | левая (left)
Логическое ИЛИ     | LogicalDisjunctionPrecedence | `\|\|`      | левая (left)
Пользовательский оператор | DefaultPrecedence            |             | нет (none)
Тернарный оператор | TernaryPrecedence            | `? :`       | правая (right)
Присваивания       | AssignmentPrecedence         | `=` `*=` `/=` `%=` `+=` `-=` | правая (right)

>  В таблице в колонке с примерами указаны не все операторы из соответствующих групп, а только часто используемые. Полный список операторов указан выше, в соответствующей группе.

## Унарные операторы

В дополнение к бинарным операторам, которые принимают два операнда, существуют также унарные операторы, которые принимают один операнд. Унарные опраторы не имеют приоритета (так как они сразу изменяют значение операнда при чтении операнда) и ассоциативности (так как нельзя указать несколько унарных операторов вместе).

### Префиксные операторы

Префиксные операторы стоят перед выражением, с которым они работают. Swift определяет несколько из них по умолчанию:

- `+` - Унарный плюс
- `-` - Унарный минус
- `!` - Логическое НЕ
- `~` - Побитовое НЕ
- `..<` - Полуоткрытый частичный диапазон
- `...` - Закрытый частичный диапазон

Например, префиксный оператор `!` инвертирует логическое значение своего операнда, а префиксный оператор `-` инвертирует числовое значение своего операнда.

```swift
!true // false
-(1.0 + 2.0) // -3.0
```

### Постфиксные операторы

Унарные операторы также могут стоять после своего операнда. Они менее распространены.

Стандартная библиотека Swift объявляет только постфиксный оператор закрытого диапазона,

- `...` - Закрытый частичный диапазон

```swift
let fruits = ["🍎", "🍌", "🍐", "🍊", "🍋"]
fruits[3...] // ["🍊", "🍋"]
```

### Тернарные операторы

Тернарный оператор `?  :` особенный. Он принимает три операнда и выполняет такие же функции, как однострочный оператор `if-else`: оценить логическое условие в левой части `?` и выполняет выражение слева или справа от `:` в зависимости от результата:

```swift
true ? "Yes" : "No" // "Yes"
```

В Swift TernaryPrecedence определяется ниже, чем DefaultPrecedence, и выше, чем AssignmentPrecedence. Но в целом лучше сделать использование тернарного оператора простым (или вообще избегать использования).

---

## Еще полезные ссылки

- [Переменные и константы](https://robot.obo.dev/read/posts/variable/)
- [Операторы](https://robot.obo.dev/read/posts/operator/)
- [Побитовые операторы](https://robot.obo.dev/read/posts/operator-bitwise/)
- [Перегрузка операторов. Пользовательские операторы](https://robot.obo.dev/read/posts/operator-custom/)
- [Типы данных](https://robot.obo.dev/read/posts/data-type/)
- [Литералы](https://robot.obo.dev/read/posts/literal/)
- [Опционалы](https://robot.obo.dev/read/posts/optional-data-type/)
- [Функции](https://robot.obo.dev/read/posts/function/)

Также информацию по операторам можно получить на странице официальной документации.

Ссылки на официальную документацию:

- [Apple Developer Documentation - Operator Declarations](https://developer.apple.com/documentation/swift/operator-declarations)
- [Swift.org - Precedence and Associativity](https://docs.swift.org/swift-book/LanguageGuide/AdvancedOperators.html#ID41)
- [Swift.org - Operator Declaration](https://docs.swift.org/swift-book/ReferenceManual/Declarations.html#ID380)