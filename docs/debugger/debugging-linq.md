---
title: Отладка LINQ | Документация Майкрософт
description: Выполните отладку LINQ в Visual Studio. Просмотрите результаты LINQ. Узнайте о различиях в поведении при пошаговом выполнении кода LINQ.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e4940c6aa1d775389ab29eeb92fc29523ef115bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872655"
---
# <a name="debugging-linq"></a>Отладка LINQ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с некоторыми ограничениями поддерживает отладку кода встроенного языка запросов (LINQ). Большинство возможностей отладки работают с операторами LINQ, включая пошаговое выполнение, установку точек останова и просмотр результатов в окнах отладчика. В этом разделе описаны основные ограничения, связанные с отладкой кода LINQ.

## <a name="viewing-linq-results"></a><a name="BKMK_ViewingLINQResults"></a> Просмотр результатов оператора LINQ
 Можно просмотреть результаты инструкции LINQ с помощью окна подсказок, окна "Контрольные значения" и диалогового окна "Быстрая проверка". При работе в окне исходного кода, можно ненадолго остановить указатель мыши на запросе в окне исходного кода для того, чтобы появилась подсказка. Можно скопировать переменную LINQ и вставить её в окно "Контрольные значения" или диалоговое окно "Быстрая проверка".

 В LINQ запрос вычисляется не при его создании или объявлении, а только при использовании. Таким образом, запросу не присваивается значение до тех пор, пока оно не будет вычислено. Полное описание создания и оценки запросов см. в статьях [Общие сведения о запросах LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) или [Создание первого запроса LINQ](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query).

 Для отображения результата запроса отладчик должен его вычислить. Это неявное вычисление, которое происходит при просмотре результатов запроса LINQ в отладчике, имеет некоторые эффекты, о которых следует знать:

- Каждое вычисление запроса занимает время. Разворачивание узла результатов занимает время. Для некоторых запросов повторное вычисление может обернуться заметной потерей производительности.

- Вычисление запроса может привести к побочным эффектам, таким как изменение значений данных или состояния программы. Не все запросы имеют побочные эффекты. Чтобы определить, может ли запрос быть безопасно вычислен без побочных эффектов, необходимо понимать код, который реализует запрос.

## <a name="stepping-and-linq"></a><a name="BKMK_SteppingAndLinq"></a> Пошаговое выполнение и LINQ
 Пошаговое выполнение при отладке кода LINQ имеет ряд особенностей, о которых следует знать.

### <a name="linq-to-sql"></a>LINQ to SQL
 При запросах из LINQ в SQL код предиката недоступен для отладчика. Соответственно, выполнить пошаговый заход в код предиката невозможно. Любой запрос, который компилируется в дерево выражения, дает в результате код, недоступный отладчику.

### <a name="stepping-in-visual-basic"></a>Пошаговое выполнение в Visual Basic
 Если при пошаговой отладке программы на Visual Basic отладчик встречает объявление запроса, он не выполняет вход в объявление, а выделяет все объявление как единый оператор. Это происходит по причине того, что до вызова запрос не разбирается. Дополнительные сведения см. в статье [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq).

 При пошаговой отладке следующего кода отладчик выделит объявление запроса, также называемое созданием запроса, как единый оператор.

```vb
Function MyFunction(ByVal x As Char)
    Return True
End Function

Sub Main()
    'Query creation
    Dim x = From it In "faoaoeua" _
            Where MyFunction(it) _
            Select New With {.a = it}

    ' Query execution
    For Each cur In x
        Console.WriteLine(cur.ToString())
    Next
End Sub
```

 Если сделать еще один шаг, отладчик выделит `For Each cur In x`. На следующем шаге он зайдет в функцию `MyFunction`. После пошагового выполнения `MyFunction` он перейдет обратно в `Console.WriteLine(cur.ToSting())`. Ни на одном этапе отладчик не пройдет по коду предиката в объявлении запроса, хотя отладчик будет разбирать этот код.

### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>Замена предиката функцией для включения пошагового режима (Visual Basic)
 Если в целях отладки необходимо пошаговое выполнение кода предиката, можно заменить предикат на вызов функции, которая содержит исходный текст кода предиката. Например, рассмотрим такой код:

```vb
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

' Get the even numbers
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt

For each item in query
      Console.WriteLine(item)
Next
```

 Можно переместить код предиката в новую функцию с именем `IsEven`:

```vb
Dim items () as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

' Get the even numbers
Dim query = From nextInt in items Where IsEven(nextInt) Select nextInt

For each item in query
      Console.WriteLine(item)
Next
...
Function IsEven(item As =Integer) as Boolean
      Return item Mod 2 = 0
End Function
```

 Измененный запрос вызывает функцию `IsEven` при каждом проходе через `items`. Чтобы проверить, выполняется ли для каждого элемента заданное условие, можно использовать окна отладчика или пройти по коду в пошаговом режиме в `IsEven`. Предикат в этом примере достаточно прост. Тем не менее, при отладке более сложных предикатов этот метод может оказаться весьма полезным.

## <a name="edit-and-continue-not-supported-for-linq"></a><a name="BKMK_EditandContinueNotSupportedforLINQ"></a> Операция "Изменить и продолжить" для LINQ не поддерживается
 Операция "Изменить и продолжить" поддерживает изменения запросов LINQ с некоторыми ограничениями. Дополнительные сведения см. в разделе [Поддерживаемые изменения EnC](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md).

## <a name="see-also"></a>См. также

- [Отладка SQL](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6\(v\=vs.100\))
- [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md)
- [Введение в запросы LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
- [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq) (Знакомство с LINQ в Visual Basic)
