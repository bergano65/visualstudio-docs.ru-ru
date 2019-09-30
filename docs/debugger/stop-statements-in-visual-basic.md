---
title: Операторы завершения в Visual Basic | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f9ab4ef453a921371ab7ef4f272cd0e38f4108a
ms.sourcegitcommit: 4d2620bee4688fb881e09a07ea4a264b99f0743e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322536"
---
# <a name="stop-statements-in-visual-basic"></a>Оператор Stop в Visual Basic

Оператор "Stop" в Visual Basic является программной альтернативой заданию точки останова. Когда отладчик встречает оператор "Stop", он прерывает выполнение программы (переходит в режим приостановки выполнения). C#программисты могут добиться того же результата, используя вызов <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>.

Оператор "Stop" задается и удаляется путем редактирования исходного кода. В отличие от точки останова его невозможно задать или удалить с помощью команд отладчика.

В отличие от оператора "End" оператор "Stop" не сбрасывает значения переменных и не переводит приложение в режим разработки. Для продолжения выполнения приложения можно выбрать пункт "Продолжить" в меню "Отладка".

При запуске приложения Visual Basic вне отладчика оператор «завершение» запускает отладчик, если JIT-отладка включена. Если JIT-отладка не включена, оператор "остановить" ведет себя так, как если бы он был оператором End, и завершает выполнение. При этом события "QueryUnload" и "Unload" не возникают, поэтому в выпускаемой версии приложения Visual Basic необходимо удалить все операторы "Stop". Дополнительные сведения см. в разделе [JIT-отладка](just-in-time-debugging-in-visual-studio.md).

 Чтобы избежать необходимости удаления операторов "Stop", можно использовать условную компиляцию:

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

Другой альтернативой является использование <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> оператора вместо оператора «останавливаться». Оператор <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> прерывает выполнение, только если не выполнено указанное условие. <xref:System.Diagnostics.Debug.Assert%2A>инструкции автоматически удаляются при сборке окончательной версии. Дополнительные сведения см. в разделе [Утверждения в управляемом коде](assertions-in-managed-code.md). Если вам нужна <xref:System.Diagnostics.Debug.Assert%2A> инструкция, которая всегда прерывает выполнение в отладочной версии, это можно сделать следующим образом:

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

Еще один вариант — использовать <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> метод:

```csharp
Debug.Fail("a clever output string goes here");
```

```vb
Debug.Fail("a clever output string goes here")
```

## <a name="see-also"></a>См. также

- [Безопасность отладчика](debugger-security.md)
- [Типы проектов C#, F# и Visual Basic](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Отладка управляемого кода](debugging-managed-code.md)
