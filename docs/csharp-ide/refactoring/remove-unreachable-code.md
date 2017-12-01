---
title: "Удалите недостижимый код - рефакторинг (C#) | Документы Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.openlocfilehash: d4dfc63000fe6f66135d452b9a64e14dc05101d9
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/29/2017
---
# <a name="remove-unreachable-code-in-c"></a>Удалите недостижимый код на языке C# #
**Что:** удаляет код, который никогда не будет выполняться.

**Когда:** приложении есть нет пути для фрагмента кода, что делает этот фрагмент кода ненужной.

**Почему:** повысить удобочитаемость и обслуживаемость, удалив код, который является избыточным и никогда не будет выполняться.

**Как:**

1. Поместите курсор в любом месте в Проявление с out код, который недоступен:

![Потеря недостижимый код](media/unreachablecode_faded.png)  

1. Затем выполните одно из следующих действий.
   * **Клавиатура**
     * Нажмите клавишу **Ctrl +.** для запуска **Быстрые действия и рефакторинг** и выбрать пункт **удалите недостижимый код** из контекстного меню окна предварительного просмотра.
   * **Мышь**
     * Щелкните его правой кнопкой мыши, выберите **Быстрые действия и рефакторинг** и выбрать пункт **удалите недостижимый код** из контекстного меню окна предварительного просмотра.

1. Если вы довольны изменения, нажмите клавишу **ввод** или выберите команду в меню, и изменения будут зафиксированы.

Пример.
```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>См. также  
[Рефакторинг (C#)](../refactoring-csharp.md)  
[Просмотр изменений](../../ide/preview-changes.md)