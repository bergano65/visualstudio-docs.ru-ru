---
title: Операторы Stop в Visual Basic | Документация Майкрософт
description: Сведения об операторе Stop в Visual Basic, который является программной альтернативой заданию точки останова в Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a17aafd508acd9272e8058ea7ca3ff585a8c0c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904942"
---
# <a name="stop-statements-in-visual-basic"></a>Оператор Stop в Visual Basic

Оператор "Stop" в Visual Basic является программной альтернативой заданию точки останова. Когда отладчик встречает оператор "Stop", он прерывает выполнение программы (переходит в режим приостановки выполнения). Программисты C# могут добиться того же результата с помощью вызова <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>.

Оператор "Stop" задается и удаляется путем редактирования исходного кода. В отличие от точки останова его невозможно задать или удалить с помощью команд отладчика.

В отличие от оператора "End" оператор "Stop" не сбрасывает значения переменных и не переводит приложение в режим разработки. Для продолжения выполнения приложения можно выбрать пункт "Продолжить" в меню "Отладка".

При запуске приложения Visual Basic вне отладчика оператор Stop запускает отладчик, если включена JIT-отладка. Если JIT-отладка не включена, оператор Stop завершит выполнение, как если бы это был оператор End. При этом события "QueryUnload" и "Unload" не возникают, поэтому в выпускаемой версии приложения Visual Basic необходимо удалить все операторы "Stop". Дополнительные сведения см. в разделе [JIT-отладка](just-in-time-debugging-in-visual-studio.md).

 Чтобы избежать необходимости удаления операторов "Stop", можно использовать условную компиляцию:

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

Другой вариант — воспользоваться оператором <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> вместо оператора Stop. Оператор <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> прерывает выполнение, только если не выполнено указанное условие. Операторы <xref:System.Diagnostics.Debug.Assert%2A> автоматически удаляются при сборке версии выпуска. Дополнительные сведения см. в разделе [Утверждения в управляемом коде](assertions-in-managed-code.md). Если требуется, чтобы оператор <xref:System.Diagnostics.Debug.Assert%2A> всегда прерывал выполнение программы в отладочной версии, сделайте следующее:

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

И еще один вариант — использовать метод <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>:

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
