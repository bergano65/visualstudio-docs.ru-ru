---
title: "Быстрые действия | Документы Майкрософт"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.openlocfilehash: e9196f3e4bc76e53d50bc480b8e0860186fe778e
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2017
---
# <a name="quick-actions"></a>Быстрые действия

[Быстрые действия](refactoring-code-generation-quick-actions.md#quick-actions) позволяют легко создавать и изменять код, а также выполнять его рефакторинг одним действием. Быстрые действия доступны для C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) и файлов кода Visual Basic. Некоторые действия доступны только для определенного языка, тогда как другие доступны для всех языков. Быстрые действия можно применять, используя значок лампочки ![Маленький значок лампочки](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") или сочетание клавиш **CTRL** + **,** когда курсор находится на подходящей строке кода.

Лампочка видна, если проблема подчеркнута красной волнистой линией и Visual Studio предлагает способ ее исправления. Например, если имеется ошибка, подчеркнутая красной волнистой линией, лампочка загорится, когда станут доступны пути исправления этой ошибки. Сторонние разработчики могут предоставить для любого языка пользовательскую диагностику и предложения, например в рамках SDK, и лампочки Visual Studio будут появляться на основе этих правил.

## <a name="to-see-a-light-bulb"></a>Отображение лампочки

1. Во многих случаях лампочки самопроизвольно появляются при наведении указателя мыши в момент ошибки или в левом поле редактора при перемещении курсора в строку, которая содержит ошибку. Если вы видите красную волнистую линию, наведите на нее курсор, чтобы появилась лампочка. Также можно включить отображение лампочки при использовании мыши или клавиатуры для перехода к строке, где возникла проблема.

1. Нажмите клавиши **CTRL** + **.** в любом месте строки, чтобы обойти лампочку и перейти непосредственно к списку возможных исправлений.

   ![Лампочка с наведением указателя мыши](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")

## <a name="to-see-potential-fixes"></a>Просмотр возможных исправлений

Щелкните стрелку вниз или ссылку "Показать возможные исправления", чтобы увидеть список быстрых действий, которые может предпринять лампочка.

![Расширенная лампочка](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## <a name="common-quick-actions"></a>Распространенные быстрые действия

Вот некоторые распространенные быстрые действия, которые применяются как к коду C#, так и к коду Visual Basic:

- [Действия для исправления ошибок](#fix)
- [Действия для удаления ненужного кода](#remove)
- [Действия для добавления недостающего кода](#add)
- [Преобразование кода](#transform)

### <a id="fix"></a> Действия для исправления ошибок

#### <a name="correct-misspelled-symbol-or-keyword"></a>Исправление опечаток в символах или ключевых словах

|  Идентификатор ошибки | Применимые языки |  Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| CS0103, BC30002 | C# и Visual Basic | Visual Studio 2015 с обновлением 2 |

Если вы неправильно напишете тип или ключевое слово в Visual Studio, это быстрое действие автоматически исправит его. Эти слова отобразятся в меню лампочки: **Изменить* слово с опечаткой* на *правильное слово***.  Пример:

```csharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

#### <a name="resolve-git-merge-conflict"></a>Разрешение конфликтов слияния Git

|  Идентификатор ошибки | Применимые языки |  Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| CS8300, BC37284  | C# и Visual Basic | Visual Studio 2017 версия 15.3 |

Эти быстрые действия позволяют устранить конфликты слияния Git, "применяя изменения", то есть удаляя конфликтующие маркеры и код.  

```csharp
// Before
private void MyMethod()
{
<<<<<<< HEAD
    if (true)
    {

    }
=======
    if (false)
    {

    }
>>>>>>> upstream
}

// Take changes from 'HEAD'

// After
private void MyMethod()
{
    if (true)
    {

    }
}
```

#### <a name="make-method-synchronous"></a>Превращение метода в синхронный

|  Идентификатор ошибки | Применимые языки |  Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| CS1998, BC42356 | C# и Visual Basic | Visual Studio 2015 с обновлением 2 |

При использовании ключевого слова `async` или `Async` для метода ожидается, что где-нибудь внутри этого метода также будет использоваться ключевое слово `await` или `Await`.  Но если это не так, отобразится быстрое действие, которое позволяет сделать метод синхронным, удалив ключевое слово `async` или `Async` и изменив тип возвращаемого значения. Используйте параметр **Синхронизация метода** в меню быстрых действий.

```csharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```vb
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

#### <a name="make-method-asynchronous"></a>Превращение метода в асинхронный

|  Идентификатор ошибки | Применимые языки |  Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| CS4032, BC37057 | C# и Visual Basic | Visual Studio 2017 |

При использовании ключевого слова `await` или `Await` внутри метода предполагается, что сам метод помечен ключевым словом `async` или `Async`.  Однако, если это не так, отображается данное быстрое действие, позволяющее сделать метод асинхронным. Используйте параметр **Make method/Function asynchronous** (Сделать метод/функцию асинхронными) в меню быстрых действий.

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method asynchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method asynchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

### <a id="remove"></a> Действия для удаления ненужного кода

#### <a name="remove-unnecesary-usingsimports"></a>Удаление ненужных операторов using/Import

|  Применимые языки |  Поддерживаемая версия |
|  -------------------- | ----------------  |
|  C# и Visual Basic | Visual Studio 2015 RTW |

Быстрое действие **Удалить ненужные директивы using/импорты** удалит все неиспользуемые операторы `using` и `Import` для текущего файла.  При выборе этого элемента неиспользованные директивы import пространства имен немедленно удаляются.

#### <a name="remove-unnecessary-cast"></a>Удаление ненужного приведения

|  ИД диагностики | Применимые языки |  Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| IDE0004 | C# и Visual Basic | Visual Studio 2015 RTW |

Если вы приводите тип к другому типу, которому приведение не требуется, быстрое действие **Удалить ненужное приведение** приведет к удалению приведения из кода.

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

#### <a name="remove-unused-variables"></a>Удаление неиспользуемых переменных

|  ИД диагностики | Применимые языки |  Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| CS0219, BC42024 | C# и Visual Basic | Visual Studio 2017 версия 15.3 |

Это быстрое действие позволяет удалить объявленные переменные, которые нигде не используются.

```csharp
// Before
public MyMethod()
{
    var unused = 8;
    var used = 1;
    return DoStuff(used);
}

// Remove unused variables

// After
public MyMethod()
{
    var used = 1;
    return DoStuff(used);
}
```

#### <a name="remove-type-from-default-value-expression"></a>Удаление типа из выражения значения **по умолчанию**

|  ИД диагностики | Применимые языки |  Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| IDE0034 | C# 7.1+ | Visual Studio 2017 версия 15.3 |

Это быстрое действие удаляет тип значения из выражения значения по умолчанию и использует [литерал `default`](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), если компилятор может вывести тип выражения.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }

```

### <a id="add"></a> Действия для добавления недостающего кода

#### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Добавление директив using/Imports для типов в ссылочных сборках, пакетах NuGet или других типов в решении

|  ИД диагностики | Применимые языки |  Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| CS0103, BC30451 | C# и Visual Basic| Visual Studio 2015 с обновлением 2 |

При использовании типов, расположенных в других проектах вашего решения, автоматически появляется быстрое действие, но другие нужно включить на вкладке **Сервис > Параметры > C#** или **Basic > Дополнительно**:

- Предлагать using/import для типов в эталонных сборках
- Предлагать using/import для типов в пакетах NuGet

Когда параметр включен, при использовании типа в пространстве имен, которое еще не импортировано, но существует в ссылочной сборке или пакете NuGet, создается оператор using/import.

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

#### <a name="add-missing-casesdefault-caseboth"></a>Добавление отсутствующих элементов case и/или case по умолчанию

|  ИД диагностики | Применимые языки |  Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| IDE0010 | C# и Visual Basic| Visual Studio 2017 версия 15.3 |

При создании оператора `switch` на языке C# или оператора `Select Case` на Visual Basic можно использовать действие кода, чтобы автоматически добавить отсутствующие элементы case и/или оператор case по умолчанию.

Используйте следующее перечисление и удалите оператор `switch` или `Select Case`:

```csharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```vb
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

Быстрое действие **Добавить оба** заполняет отсутствующие элементы case и добавляет элементы case по умолчанию.

```csharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```

```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

#### <a name="add-null-checks-for-parameters"></a>Добавление проверки null для параметров

| Применимые языки |  Поддерживаемая версия |
| -------------------- | ----------------  |
| C# и Visual Basic| Visual Studio 2017 версия 15.3 |

Это быстрое действие позволяет добавить в код проверку параметра на значение Null.

```csharp
// Before
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty) // cursor inside myProperty
    {
        MyProperty = myProperty;
    }
}

// Add null check

// After
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty)
    {
        MyProperty = myProperty ?? throw new ArgumentNullException(nameof(myProperty));
    }
}
```

#### <a name="add-argument-name"></a>Добавление имени аргумента

| Применимые языки |  Поддерживаемая версия |
| -------------------- | ----------------  |
| C# и Visual Basic| Visual Studio 2017 версия 15.3 |

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

#### <a name="add-braces"></a>Добавление фигурных скобок

|  ИД диагностики | Применимые языки |  Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| IDE0011 | C# | Visual Studio 2017 RTW |

Быстрое действие "Добавить фигурные скобки" заключает в скобки однострочные операторы `if`.

```csharp
// Before
if (true)
    return "hello,world";

// Add braces

// After
if (true)
{
    return "hello,world";
}
```

#### <a name="add-and-order-modifiers"></a>Добавление и упорядочивание модификаторов

|  ИД диагностики | Применимые языки |  Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| IDE0036 | C# и Visual Basic| Visual Studio 2017 версии 15.5 |
| IDE0040 | C# и Visual Basic| Visual Studio 2017 версии 15.5 |

Эти быстрые действия помогают отсортировать имеющиеся модификаторы доступа и добавить недостающие.

```csharp
// Before
enum Color
{
    Red, White, Blue
}

// Add accessibility modifiers

// After
internal enum Color
{
    Red, White, Blue
}
```

```csharp
// Before
static private int thisFieldIsPublic;

// Order modifiers

// After
private static int thisFieldIsPublic;
```

### <a id="transform"></a> Преобразование кода

#### <a name="convert-if-construct-to-switch"></a>Преобразование конструкции **if** в конструкцию **switch**

| Применимые языки |  Поддерживаемая версия |
| -------------------- | ----------------  |
| C# и Visual Basic| Visual Studio 2017 версия 15.3 |

Это быстрое действие позволяет преобразовать конструкцию **if-then-else** в конструкцию **switch**.

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

#### <a name="convert-to-interpolated-string"></a>Преобразование в интерполированную строку

| Применимые языки |  Поддерживаемая версия |
| -------------------- | ----------------  |
| C# 6.0+ и Visual Basic 14+ | Visual Studio 2017 RTW |

[Интерполированные строки](/dotnet/csharp/language-reference/keywords/interpolated-strings) позволяют легко выразить строки с внедренными переменными по аналогии с методом **[String.Format](https://msdn.microsoft.com/library/system.string.format.aspx)**.  Это быстрое действие распознает использование сцепленных строк или оператора **String.Format** и переключается на использование интерполированной строки.

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

#### <a name="use-object-initializers"></a>Использование инициализаторов объектов

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| IDE0017 | C# и Visual Basic | Visual Studio 2017 RTW |

Это быстрое действие позволяет использовать [инициализаторы объектов](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md), чтобы не вызывать конструктор и не добавлять строки операторов назначения.

```csharp
// Before
var c = new Customer();
c.Age = 21;

// Object initialization can be simplified

// After
var c = new Customer() { Age = 21 };
```

```vb
' Before
Dim c = New Customer()
c.Age = 21

' Object initialization can be simplified

' After
Dim c = New Customer() With {.Age = 21}
```

#### <a name="use-collection-initializers"></a>Использование инициализаторов набора

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| IDE0028 | C# и Visual Basic | Visual Studio 2017 RTW |

Это быстрое действие позволяет использовать [инициализаторы набора](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md), чтобы не вызывать несколько раз метод `Add` из вашего класса.

```csharp
// Before
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);

// Collection initialization can be simplified

// After
var list = new List<int> { 1, 2, 3 };
```

```vb
' Before
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)

' Collection initialization can be simplified

' After
Dim list = New List(Of Integer) From {1, 2, 3}

```

#### <a name="convert-auto-property-to-full-property"></a>Преобразование автосвойства в полное свойство

|  Применимые языки |  Поддерживаемая версия |
|  -------------------- | ----------------  |
| C# и Visual Basic | Visual Studio 2017 версии 15.5 |

Это быстрое действие позволяет преобразовать автосвойство в полное свойство, и наоборот.

```csharp
// Before
private int MyProperty { get; set; }

// Convert to full property

// After
private int MyProperty
{
    get { return _myProperty; }
    set { _myProperty = value; }
}
```

```vb
' Before
Public Property Name As String

' Convert to full property

' After
Private _Name As String

Public Property Name As String
    Get
        Return _Name
    End Get
    Set
        _Name = Value
    End Set
End Property
```

#### <a name="convert-block-body-to-expression-bodied-member"></a>Преобразование тела блока в элемент с телом выражения

|  ИД диагностики | Применимые языки |  Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| IDE0021-27 | C# 6.0+ | Visual Studio 2017 RTW |

Это быстрое действие позволяет преобразовать тело блока в элемент с телом выражения. Оно предназначено для методов, конструкторов, операторов, свойств, индексаторов и методов доступа.

```csharp
//Before
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get { return _myProperty; }
        set
        {
            _myProperty = value;
        }
    }

    public MyClass4(int myProperty)
    {
        MyProperty = myProperty;
    }

    public void PrintProperty()
    {
        Console.WriteLine(MyProperty);
    }
}

// Use expression body for accessors/constructors/methods

// After
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get => _myProperty;
        set => _myProperty = value;
    }

    public MyClass4(int myProperty) => MyProperty = myProperty;

    public void PrintProperty() => Console.WriteLine(MyProperty);
}
```

#### <a name="convert-anonymous-function-to-local-function"></a>Преобразование анонимной функции в локальную

|  ИД диагностики | Применимые языки |  Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| IDE0039 | C# 7.0+ | Visual Studio 2017 версии 15.5 |

Это быстрое действие преобразует анонимные функции в локальные.

```csharp
// Before
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};

// Use local function

// After
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}
```

#### <a name="convert-referenceequals-to-is-null"></a>Преобразование `ReferenceEquals` в `is null`

|  ИД диагностики | Применимые языки |  Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| IDE0041 | C# 7.0+ | Visual Studio 2017 версии 15.5 |

Это быстрое действие предлагает использовать [сопоставление шаблонов](/dotnet/csharp/pattern-matching), а не шаблон кода ```ReferenceEquals```, где это возможно.

```csharp
// Before
var value = "someString";
if (object.ReferenceEquals(value, null))
{
    return;
}

// Use 'is null' check

// After
var value = "someString";
if (value is null)
{
    return;
}
```

#### <a name="introduce-pattern-matching"></a>Введение сопоставления шаблонов

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| IDE0020 | C# 7.0+ | Visual Studio 2017 RTW |
| IDE0019 | C# 7.0+ | Visual Studio 2017 RTW |

Это быстрое действие предлагает использовать [сопоставление шаблонов](/dotnet/csharp/pattern-matching) с приведениями и проверкой на NULL в C#.   

```csharp
// Before
if (o is int)
{
    var i = (int)o;
    ...
}

// Use pattern matching

// After
if (o is int i)
{
    ...
}

```

```csharp
// Before
var s = o as string;
if (s != null)
{
    ...
}

// Use pattern matching

// After
if (o is string s)
{
    ...
}
```

#### <a name="change-base-for-numeric-literals"></a>Изменение основания для числовых литералов

| Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| C# 7.0 и более поздние версии, Visual Basic 14 и более поздние версии | Visual Studio 2017 версия 15.3 |

Это быстрое действие позволяет преобразовать числовой литерал в систему счисления с другим основанием. Например, можно перевести любое шестнадцатеричное число в двоичное. 

```csharp
// Before
int countdown = 2097152;

// Convert to hex

// After
int countdown = 0x200000;
```

```vb
' Before
Dim countdown As Integer = 2097152

' Convert to hex

' After
Dim countdown As Integer = &H200000
```

#### <a name="insert-digit-separators-into-literals"></a>Добавление разделителей между цифрами в литералах

| Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| C# 7.0 и более поздние версии, Visual Basic 14 и более поздние версии | Visual Studio 2017 версия 15.3 |

Это быстрое действие позволяет добавлять знаки-разделители в литеральные значения.

```csharp
// Before
int countdown = 1000000;

// Separate thousands

// After
int countdown = 1_000_000;
```

```vb
' Before
Dim countdown As Integer = 1000000

' Separate thousands

' After
Dim countdown As Integer = 1_000_000
```

#### <a name="use-explicit-tuple-names"></a>Использование явных имен кортежей

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| IDE0033 | C# 7.0+ и Visual Basic 15+ | Visual Studio 2017 RTW |

Это быстрое действие выявляет области, где можно использовать явные имена кортежей вместо Item1, Item2 и т. д.

```csharp
// Before
(string name, int age) customer = GetCustomer();
var name = customer.Item1;

// Use explicit tuple name

// After
(string name, int age) customer = GetCustomer();
var name = customer.name;
```

```vb
' Before
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1

' Use explicit tuple name

' After
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name
```

#### <a name="use-inferred-names"></a>Использование выводимых имен

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| IDE0037 | C# | Visual Studio 2017 версии 15.5 |
| IDE0037 | C# 7.1+ | Visual Studio 2017 версии 15.5 |

Эти быстрые действия сообщают, когда пользователи могут применять выводимые имена элементов в анонимных типах или выводимые имена элементов кортежей C# 7.1.

```csharp
// Before
var anon = new { age = age, name = name };

// Use inferred member name

// After
var anon = new { age, name };
```

```csharp
// Before
var tuple = (age: age, name: name);

// Use inferred tuple element name

// After
var tuple = (age, name);
```

#### <a name="deconstruct-tuple-declaration"></a>Деконструирование объявления кортежа

| ИД диагностики | Применимые языки | Поддерживаемая версия |
| ------- | -------------------- | ----------------  |
| IDE0042 | C# 7.0+ | Visual Studio 2017 версии 15.5 |

Это быстрое действие позволяет деконструировать объявления переменных в кортежах. 

```csharp
// Before
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");

//Deconstruct variable declaration

// After
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");
```

## <a name="see-also"></a>См. также

[Стили кода и быстрые действия](code-styles-and-quick-actions.md)  
[Написание и рефакторинг кода (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
