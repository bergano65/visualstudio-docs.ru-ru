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
ms.openlocfilehash: 7893ed676372cce94d883353139de91ef639aeb0
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531851"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Преобразование цикла foreach в LINQ

Область применения этого рефакторинга:

- C#

**Что?** Позволяет легко преобразовывать циклы *foreach*, использующие IEnumerables, в запрос LINQ или форму вызова LINQ (также известную как метод LINQ).

**Когда?** У вас есть цикл foreach, использующий IEnumerable, и вам нужно, чтобы цикл читался как запрос LINQ.

**Зачем?** Вы предпочитаете использовать синтаксис LINQ, а не цикл foreach. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) выполняет запрос в удобной языковой конструкции в C#. LINQ может уменьшить объем кода в файле, сделать код более удобным для чтения и разрешить разным источникам данных иметь схожие шаблоны выражений запроса.

> [!NOTE]
> Как правило, синтаксис LINQ менее эффективен, чем цикл foreach. Рекомендуется учитывать все компромиссы в производительности при использовании LINQ для улучшения читаемости кода.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Рефакторинг "Преобразование цикла foreach в LINQ"

1. Поместите курсор в ключевое слово `foreach`.

    ![Пример foreach с IEnumerable](media/convert-foreach-to-LINQ.png)

2. Нажмите клавиши **CTRL**+**.** чтобы открыть меню **Быстрые действия и рефакторинг**.

   ![Пример меню преобразования в LINQ](media/convert-foreach-to-LINQ-codefix.png)

3. Выберите параметр **преобразования в LINQ** или **преобразования в форму вызова LINQ**.

   ![Пример результата преобразования в запрос LINQ](media/convert-foreach-to-LINQ-result.png)

   ![Пример результата преобразования в форму вызова LINQ](media/convert-foreach-to-LINQ-callform-result.png)

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
- [Окно просмотра изменений](../../ide/preview-changes.md)
- [Советы для разработчиков .NET](../csharp-developer-productivity.md)
