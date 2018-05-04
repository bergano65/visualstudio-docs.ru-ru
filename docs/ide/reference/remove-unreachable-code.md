---
title: Рефакторинг для удаления недоступного кода в Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: douge
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 73b04dafc094e05c57c626333a1d614de3ba76a1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="remove-unreachable-code-refactoring"></a>Рефакторинг для удаления недоступного кода

Область применения этого рефакторинга:

- C#

**Что.** Удаление кода, который никогда не будет выполняться.

**Когда.** У приложения нет пути к фрагменту кода, что делает этот фрагмент кода ненужным.

**Зачем.** Повысить удобочитаемость и удобство поддержки, удалив код, который является избыточным и никогда не будет выполняться.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в любом месте в области затемненного кода, который недоступен:

![Затемнение недоступного кода](media/unreachablecode-faded-cs.png)

1. Затем выполните одно из следующих действий:

   - **Клавиатура**
     - Нажмите клавиши **CTRL**+**.** чтобы активировать меню **Быстрые действия и рефакторинг**. Затем выберите во всплывающем окне предварительного просмотра пункт **Удалить недоступный код**.
   - **Мышь**
     - Щелкните код правой кнопкой мыши и выберите меню **Быстрые действия и рефакторинг**. Затем выберите во всплывающем окне предварительного просмотра пункт **Удалить недоступный**.

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

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)