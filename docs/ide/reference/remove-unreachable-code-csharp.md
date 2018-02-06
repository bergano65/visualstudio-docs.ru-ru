---
title: "Рефакторинг для удаления недоступного кода в C# в Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 12b6910aad6399b72b3e4bc10e6b857cc98c09bb
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2018
---
# <a name="remove-unreachable-code-in-c"></a>Удаление недоступного кода в C# #

**Что.** Удаление кода, который никогда не будет выполняться.

**Когда.** У приложения нет пути к фрагменту кода, что делает этот фрагмент кода ненужным.

**Зачем.** Повысить удобочитаемость и удобство поддержки, удалив код, который является избыточным и никогда не будет выполняться.

**Как.**

1. Поместите курсор в любом месте в области затемненного кода, который недоступен:

![Затемнение недоступного кода](media/unreachablecode-faded-cs.png)

1. Затем сделайте следующее:
   * **Клавиатура**
     * Нажмите клавиши **CTRL+.**, чтобы активировать меню **Быстрые действия и рефакторинг**. Затем выберите во всплывающем окне предварительного просмотра пункт **Удалить недоступный код**.
   * **Мышь**
     * Щелкните код правой кнопкой мыши и выберите меню **Быстрые действия и рефакторинг**. Затем выберите во всплывающем окне предварительного просмотра пункт **Удалить недоступный**.

1. Если вы довольны результатами, нажмите клавишу **ВВОД** или выберите соответствующий пункт в меню, чтобы зафиксировать изменения.

Пример

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

[Рефакторинг](../refactoring-in-visual-studio.md)  
[Просмотр изменений](../../ide/preview-changes.md)