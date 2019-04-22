---
title: Преобразование цикла foreach в LINQ
ms.date: 02/20/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 18c5b01aed925bf458e1c8779a2f41ea1a2d98a4
ms.sourcegitcommit: 7eb85d296146186e7a39a17f628866817858ffb0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2019
ms.locfileid: "59504072"
---
# <a name="convert-foreach-loop-to-linq"></a>Преобразование цикла foreach в LINQ

Область применения этого рефакторинга:

- C#

**Что?** Позволяет легко преобразовывать циклы foreach с IEnumerables в запрос LINQ или форму вызова LINQ (также называется методом LINQ).

**Когда?** Когда у вас есть цикл foreach, использующий IEnumerable, который вы хотите читать как запрос LINQ.

**Зачем?** Иногда пользователи предпочитают использовать синтаксис LINQ вместо цикла foreach. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) делает запросы очень удобной языковой конструкцией в C#. LINQ может уменьшить объем кода в файле, сделать его более удобным для чтения и разрешить разным источникам данных иметь схожие шаблоны выражений запроса.

> [!NOTE]
> Как правило, синтаксис LINQ имеет более низкую производительность по сравнению с циклами foreach. Помните о снижении производительности, когда повышаете удобочитаемость кода с помощью LINQ.

## <a name="convert-foreach-loop-to-linq-refactoring"></a>Рефакторинг "Преобразование цикла foreach в LINQ"

1. Поместите курсор в ключевое слово `foreach`.

    ![Foreach с IEnumerable](media/convert-foreach-to-LINQ.png)

2. Нажмите клавиши **CTRL**+**.** чтобы открыть меню **Быстрые действия и рефакторинг**.

   ![Меню преобразования в LINQ](media/convert-foreach-to-LINQ-codefix.png)

3. Выберите **Преобразовать в LINQ** или **Преобразовать в LINQ (форма вызова)**

   ![Результаты преобразования в запрос LINQ](media/convert-foreach-to-LINQ-result.png)
   
   ![Результаты преобразования в форму вызова LINQ](media/convert-foreach-to-LINQ-callform-result.png)
   
### <a name="sample-code"></a>Пример кода

```csharp
using System.Collections.Generic;

public class Class1
{
    public void MyMethod()
    {
        var greetings = new List<string>()
            { "hi", "yo", "hello", "howdy" };

        IEnumerable<string> enumerable()
        {
            foreach (var greet in greetings)
            {
                if (greet.Length < 3)
                {
                    yield return greet;
                }
            }

            yield break;
        }
    }
}
```

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Просмотреть изменения](../../ide/preview-changes.md)
- [Советы для разработчиков .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
