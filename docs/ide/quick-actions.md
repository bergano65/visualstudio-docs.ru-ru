---
title: "Быстрые действия | Документы Майкрософт"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: e173fb7d-c5bd-4568-ba0f-aa61913b3244
author: BrianPeek
ms.author: brpeek
manager: ghogen
dev_langs:
- CSharp
- VB
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: 226e51ace56d51945cc380aaaf3450ae7dacf8e4
ms.lasthandoff: 03/27/2017

---
# <a name="quick-actions"></a>Быстрые действия

[Быстрые действия](refactoring-code-generation-quick-actions.md#quick-actions) позволяют легко создавать и изменять код, а также выполнять его рефакторинг одним действием.  Хотя существует много быстрых действий, которые применяются непосредственно к C# или Visual Basic, некоторые из них применяются к обоим этим видам проектов.  Их можно применять, используя значок лампочки ![маленький значок лампочки](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") или сочетание клавиш **CTRL+.**, когда курсор находится на подходящей строке кода.

Лампочка видна, если проблема подчеркнута красной волнистой линией и Visual Studio предлагает способ ее исправления. Например, если имеется ошибка, подчеркнутая красной волнистой линией, лампочка загорится, когда станут доступны пути исправления этой ошибки. Сторонние разработчики могут предоставить для любого языка пользовательскую диагностику и предложения, например в рамках SDK, и лампочки Visual Studio будут появляться на основе этих правил.  

### <a name="to-see-a-light-bulb"></a>Отображение лампочки  

1. Во многих случаях лампочки самопроизвольно появляются при наведении указателя мыши в момент ошибки или в левом поле редактора при перемещении курсора в строку, которая содержит ошибку. Если вы видите красную волнистую линию, наведите на нее курсор, чтобы появилась лампочка. Также можно включить отображение лампочки при использовании мыши или клавиатуры для перехода к строке, где возникла проблема.  

2. Нажмите клавиши **CTRL+.** в любом месте строки, чтобы обойти лампочку и перейти непосредственно к списку возможных исправлений.  

   ![Лампочка с наведением указателя мыши](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")  

### <a name="to-see-potential-fixes"></a>Просмотр возможных исправлений  
Щелкните стрелку вниз или ссылку "Показать возможные исправления", чтобы увидеть список быстрых действий, которые может предпринять лампочка.  

![Расширенная лампочка](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## <a name="common-quick-actions"></a>Распространенные быстрые действия
Ниже приведены некоторые распространенные быстрые действия, которые применяются как к коду C#, так и к коду Visual Basic.

### <a name="add-missing-casesdefault-caseboth"></a>Добавление отсутствующих элементов case и/или case по умолчанию
При создании оператора `switch` на языке C# или оператора `Select Case` на Visual Basic можно использовать действие кода, чтобы автоматически добавить отсутствующие элементы case и/или оператор case по умолчанию.  Пустой оператор представлен ниже:

```CSharp
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

```VB
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

Использование быстрого действия **Добавить оба** для заполнения отсутствующих элементов case и оператора case по умолчанию приводит к созданию следующего:

```CSharp
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

```VB
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

### <a name="correct-misspelled-type"></a>Правильный тип с опечаткой
Если вы случайно неправильно указали тип в Visual Studio, это быстрое действие автоматически исправит его.  Вы увидите эти элементы в меню лампочки в виде **"Изменить "*тип с опечаткой*" на "*правильный тип*"**.  Пример:

```CSharp
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

```VB
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

### <a name="remove-unnecessary-cast"></a>Удаление ненужного приведения
Если вы приводите тип к другому типу, которому приведение не требуется, быстрое действие **Удалить ненужное приведение** приведет к удалению приведения из кода.

```CSharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```VB
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

### <a name="replace-method-with-property--replace-property-with-method"></a>Замена метода на свойство или свойства на метод
Эти быстрые действия позволяют преобразовать метод в свойство или наоборот.  В приведенном ниже примере показана замена метода на свойство.  Чтобы добиться обратного, просто инвертируйте разделы *Before* и *After*.

```CSharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

```VB
Dim MyValue As Integer

' Before
Function GetMyValue() As Integer
    Return MyValue
End Function

' Replace 'GetMyValue' with property

' After
ReadOnly Property MyValue As Integer
    Get
        Return MyValue
    End Get
End Property
```

### <a name="make-method-synchronous"></a>Превращение метода в синхронный
При использовании ключевого слова `async`/`Async` для метода ожидается, что где-нибудь внутри этого метода также будет использоваться ключевое слово `await`/`Await`.  Однако, если это не так, отображается данное быстрое действие, позволяющее сделать метод синхронным, удалив ключевое слово `async`/`Async` и изменив тип возвращаемого значения.  Используйте параметр **Синхронизация метода** в меню быстрых действий.

```CSharp
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

```VB
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

### <a name="make-method-asynchronous"></a>Превращение метода в асинхронный
При использовании ключевого слова `await`/`Await` внутри метода предполагается, что сам метод помечен ключевым словом `async`/`Async`.  Однако, если это не так, отображается данное быстрое действие, позволяющее сделать метод асинхронным.  Используйте параметр **Make method/Function asynchronous** (Сделать метод/функцию асинхронными) в меню быстрых действий.

```CSharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method synchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```VB
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method synchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

### <a name="remove-unnecesary-usingsimports"></a>Удаление ненужных директив using/Import
Быстрое действие **Удалить ненужные директивы using/импорты** удалит все неиспользуемые операторы `using` и `Import` для текущего файла.  При выборе этого элемента неиспользованные директивы import пространства имен немедленно удаляются.

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Добавление директив using/Imports для типов в ссылочных сборках, пакетах NuGet или других типов в решении
При использовании типов, расположенных в других проектах вашего решения, автоматически появляется быстрое действие, но другие нужно включить на вкладке **Сервис > Параметры > C#** или **Basic > Дополнительно**:  

* Предлагать using/import для типов в эталонных сборках
* Предлагать using/import для типов в пакетах NuGet

Когда параметр включен, при использовании типа в пространстве имен, которое еще не импортировано, но существует в ссылочной сборке или пакете NuGet, создается оператор using/import.

```CSharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```VB
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

### <a name="convert-to-interpolated-string"></a>Преобразовать в интерполированную строку
[Интерполированные строки](/dotnet/articles/csharp/language-reference/keywords/interpolated-strings) позволяют легко выразить строки с внедренными переменными по аналогии с методом **[String.Format](https://msdn.microsoft.com/library/system.string.format(v=vs.110).aspx)**.  Это быстрое действие распознает элементы case, которые сцеплены или используют **String.Format**, а также изменяет использование интерполированной строки.

```CSharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```VB
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

# <a name="see-also"></a>См. также
* [Стили кода и быстрые действия](code-styles-and-quick-actions.md)
