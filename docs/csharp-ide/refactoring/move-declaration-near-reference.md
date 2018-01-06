---
title: "Переместить объявление рядом со ссылкой - рефакторинг (C#) | Документы Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: d79d55ae-f6bb-4902-8db2-e7fe01bdb0bf
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: c274fd758fdae468bee884fcf1686abc16ec1d7e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="move-declaration-near-reference-in-c"></a>Переместить объявление рядом со ссылкой на языке C# #
**Что:** позволяет перемещать ближе объявления переменных для их использования.

**Когда:** иметь объявления переменных, которые могут находиться в более узкой области.

**Почему:** может оставить его как это, но могут вызвать проблемы для удобства чтения или сокрытие информации. Это возможность рефакторинга для повышения удобства чтения.

**Как:**

1. Поместите курсор в объявление переменной.

1. Затем выполните одно из следующих действий.
   * **Клавиатура**
     * Нажмите клавишу **Ctrl +.** для запуска **Быстрые действия и рефакторинг** и выбрать пункт **переместить объявление рядом со ссылкой** из контекстного меню окна предварительного просмотра.
   * **Мышь**
     * Щелкните его правой кнопкой мыши, выберите **Быстрые действия и рефакторинг** и выбрать пункт **переместить объявление рядом со ссылкой** из контекстного меню окна предварительного просмотра.

1. Если вы довольны изменения, нажмите клавишу **ввод** или выберите команду в меню, и изменения будут зафиксированы.

Пример
```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>См. также  
[Рефакторинг (C#)](../refactoring-csharp.md)  
[Просмотр изменений](../../ide/preview-changes.md)