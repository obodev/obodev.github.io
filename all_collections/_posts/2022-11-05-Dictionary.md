---
layout: post
title: Коллекции. Словари (Dictionary)
date: 2022-11-05
categories: ["Swift", "SPL"]
---

# Словари (Dictionary)

Словарь еще один тип коллекций в программировании на Swift. С помощью словаря можно хранить данные в формате ключ-значение.

Словарь представляет собой контейнер, который хранит несколько значений одного и того же типа. Каждое значение связано с уникальным ключом, который выступает в качестве идентификатора этого значения внутри словаря. Словарь отличается от массива тем, что элементы в словаре не имеют определенного порядка. Необходимо использовать словарь, когда необходимо искать значения на основе их идентификатора, так же как в реальном мире словарь используется для поиска определения конкретного слова.

## Что из себя представляет словарь?

Можно использовать словарь для хранения коллекции элементов в формате ключ-значение. Словарь похож на массив в том смысле, что оба они содержат элементы только одного типа.

```swift
let scores = ["Bob": 42, "Alice": 10, "Daisy": 33]
 
print(scores)
// ["Alice": 10, "Bob": 42, "Daisy": 33]
```

Тип словаря scores [String: Int]. Это означает , что тип ключей в словаре и тип его значений являются String и Int соответственно. В приведенном выше примере мы явно не указали тип словаря, потому что Swift может вывести его из контекста. 

Вы не можете изменить тип словаря, как только он был объявлен.

Между скобками […] мы помещаем пары ключ-значение, разделенные запятыми. Ключ и значение разделяются между собой двоеточием. **Каждый ключ в словаре уникален**.

## Где используют словари

Пример структуры данных формата JSON, который широко используется различными API и веб-сервисами.

```json
[
    {
        "username": "@reinder42",
        "profile_url": "https://twitter.com/profiles/reinder42.jpg"
        "tweets": [...]
    }, {
        "username": "@arthurdent",
        "profile_url": "https://twitter.com/profiles/arthur_dent.jpg"
        "tweets": [...]
    }, {
        "username": "@xxx_darthvader1999",
        "profile_url": "https://twitter.com/profiles/darthvader.jpg"
        "tweets": [...]
    }
]
```

Если вы посмотрите внимательно, то увидите, что элемент верхнего уровня — это массив, обозначенный как [ ]. И элементы в массиве являются словарями, обозначенными { }. Они связывают ключи со значениями, такими как «username «и «@reinder42».

Можно преобразовать JSON в массив словарей Swift:

```swift
let twitter = [
    [
        "username": "@reinder42",
        "profile_url": "https://twitter.com/profiles/reinder42.jpg"
        "tweets": [···]
    ],
    ···
]
```

При переборе массива twitter с помощью цикла for вы можете получить имя пользователя Twitter с помощью:

```swift
for item in twitter
{
    let username = item["username"]
 
    // Выполнить код.
}
```

Также словари в Swift используются:

- При сохранении пользовательских настройек по умолчанию в UserDefaults.
- При сохранение значений ключей в iCloud.
- Объекты Firebase Firestore являются словарями.
- Основой файлов в формате Plist является словарь, закодированный как XML.

## Создание словаря

Когда вы создаете словарь и присваиваете его переменной, то созданная коллекция будет изменяемой. Это означает, что вы можете изменить коллекцию после ее создания путем добавления, удаления, или изменения элементов этой коллекции. И наоборот, когда вы присвоите словарь константе, то он будет неизменяемым, а его размер и содержимое не может быть изменено.

Тип словаря в Swift в полной форме пишется как **Dictionary<Key, Value>**, где *Key* - это тип значения который используется как ключ словаря, а *Value* - это тип значения который словарь может хранить для этих ключей.

При этом следует учитывать, что тип словаря *Key* должен подчиняться протоколу *Hashable*, как тип значения множества.

В сокращенной форме тип словаря можно написать как [Key: Value]. 

Хотя две формы функционально идентичны, краткая форма является предпочтительной и используется чаще.

Общая форма объявления словаря

```swift
var dict: Dictionary<String, Int> = ["Adam": 22, "Ben": 25]
```

Сокращенная форма словаря

```swift
var dict: [String: Int] = ["Adam": 22, "Ben": 25]
```

Декларирование словаря. 

```swift
var dict: Dictionary<String, Int>
```

Объявление словаря без указания типа данных (Создание словаря с литералом словаря)
```swift
var dict = ["Adam": 22, "Ben": 25]
```

Объявление пустого словаря

```swift
let scores = [String: Int]()
print(scores)
```

Еще один способ объявления пустого словаря

```swift
let scores: [String: Int] = [:]
print(scores)
```

## Работа со словарем

Можно получить доступ к словарю и изменять его либо через его методы и свойства, либо используя синтаксис индексов. 

## Работа с элементами словаря: добавление, получение, изменение и удаление элементов словаря

Расположение элементов в словаре неупорядочено. То есть пары ключ-значение в словаре не имеют порядка по умолчанию или какой-либо сортировки.

Вернемся к предыдущему примеру со словарем scores:

```swift
var scores = ["Bob": 42, "Alice": 10, "Daisy": 33]
```

Для добавления новой пары ключ-значение в словарь мы используем:

```swift
scores["Finn"] = 99
```

Приведенный выше код добавляет новый ключ «Finn» в словарь scores со значением 99. Обратите внимание, что его тип такой же, как и типы других элементов в словаре scores, то есть String для ключей и Int для значений.

### Получение и изменение элементов словаря

Начнем с получения значений из словаря:

```swift
let score = scores["Bob"]
```

При этом тип полученного значения score будет **Int?**. Это означает, что возвращаемое значение словаря является опциональным.

Почему это происходит? Потому что нельзя быть уверенным, что данный ключ существует в словаре. Когда вы используете ключ, которого нет в словаре, возвращается значение **nil**.

```swift
var scores = [
    "Bob": 42,
    "Alice": 10,
    "Daisy": 33
]
 
let score_bob = scores["Bob"]
print(score_bob)
// Optional(42)
 
let score_unknown = scores["Arthur"]
print(score_unknown)
// nil
```

Значение "score_bob" имеет тип "Optional(42)" или "Int?". Значение "score_unknown" - "nil".

Можно использовать опциональное связывание при получении значений из словаря:

```swift
if let score = scores["Bob"] {
    print(score)
}
```

Также мы можем изменить словарь с помощью похожего синтаксиса:

```swift
var scores = ["Bob": 42, "Alice": 10, "Daisy": 33]

scores["Alice"] = 101
print(scores)
// ["Alice": 101, "Bob": 42, "Daisy": 33]
```

Значение для ключа "Alice" теперь изменено на "101". Синтаксис для добавления, удаления, изменения и получения элементов из словаря по сути одинаков.

Но что, если необходимо узнать, была ли пара ключ-значение добавлена ​​в словарь или изменена по сравнению с существующей парой ключ-значение? Здесь поможет функция (метод словаря) *updateValue(_:forKey:)*.

Данный метод можно использовать в качестве альтернативы индексам, чтобы установить или обновить значение для определенного ключа. Как и с примерами работы с индексами (ключами) выше, метод *updateValue(_:forKey:)* устанавливает значение для ключа если оно не существует, или обновляет значение, если этот ключ уже существует. Однако, в отличие от индексов, метод updateValue(_:forKey:) возвращает старое значение после выполнения обновления. Это позволяет вам проверить состоялось ли обновление или нет.

```swift
if let oldScore = scores.updateValue(99, forKey: "Daisy") {
    print("Счет Daisy был: \(oldScore)")
} else {
    print("Нет игрока с данным именем...")
}
```

Данный метод возвращает одно из двух значений:

- Возвращает nil, когда ключ не присутствовал в словаре до его установки.
- Возвращает опциональное текущее значение, то есть «старое значение» ключа перед его установкой, если ключ присутствует в словаре.

Метод updateValue(_:forKey:) возвращает опциональное значение соответствующее типу значения словаря. Например, для словаря, который хранит *String* значения, метод возвратит *String?* тип, или "опциональный String".

### Удаление элементов словаря
 
Удаление элемента из словаря выполняется путем присвоения его значению nil:

```swift
scores["Alice"] = nil
```

Кроме того, можно удалить пару ключ-значение из словаря с помощью метода *removeValue(forKey:)*. Этот метод удаляет пару ключ-значение если она существует и затем возвращает значение, либо возвращает nil если значения не существует:

```swift
if let removedValue = scores.removeValue(forKey: "Alice") {
  print("The removed score value is \(removedValue).")
} else {
  print("The dictionary does not contain a value for Alice.")
}
// Выведет "The removed score value is 101."
```

## Работа со словарем

Также как и у массивов, можно узнать количество элементов в словаре через его *read-only* свойство *count*:

```swift
print("The dictionary contains \(scores.count) items.")
// Выведет "The dictionary contains 2 items."
```

Логическое свойство *isEmpty* можно использовать в качестве быстрого способа узнать, является ли свойство count равным 0:

```swift
if scores.isEmpty {
  print("The dictionary is empty.")
} else {
  print("The dictionary is not empty.")
}
// Выведет "The dictionary is not empty."
```

### Итерация по словарю

Можно сделать итерацию по парам ключ-значение в словаре с помощью for-in цикла. Каждое значение в словаре возвращается как кортеж (ключ, значение), и можно разложить части кортежа по временным константам или переменным в рамках итерации:

```swift
for (scoresName, scoresNumber) in scores {
  print("\(scoresName): \(scoresNumber)")
}
```

Также можно получить коллекцию ключей или значений словаря через обращение к его свойствам *keys* и *values*:

```swift
for scoresName in scores.keys {
  print("Player name: \(scoresName)")
}

for scoresNumber in scores.values {
  print("Player score: \(scoresNumber)")
}
```

Если необходимо использовать ключи или значения словаря вместе с каким-либо API, которое принимает объект "Array", то можно инициализировать новый массив с помощью свойств *keys* и *values*:

```swift
let scoresName = [String](scores.keys)
let scoresNumber = [String](scores.values)
```

Тип словаря в Swift является неупорядоченной коллекцией. Для итерации по ключам или значениям словаря в определенной последовательности, используйте метод sorted() для свойств keys или values словаря.