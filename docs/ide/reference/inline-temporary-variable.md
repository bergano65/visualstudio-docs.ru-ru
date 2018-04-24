---
title: Замена временной переменной ее значением в Visual Studio | Документы Майкрософт
ms.custom: ''
ms.date: 01/26/2018
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 12cce111e3c66018cd10e7e50e9018dc9dbfc4d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="inline-a-temporary-variable-refactoring"></a>Рефакторинг для замены временной переменной

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Удаление временной переменной и ее замена значением.

**Когда?** Использование временной переменной затрудняет понимание кода.

**Зачем?** Удаление временной переменной может сделать код более удобным для чтения.

## <a name="how-to"></a>Практические советы

1. Выделите временную переменную или наведите на нее курсор для замены:

   - C#:

    ![Выделенный код — C#](media/inline-highlight-cs.png)

   - Visual Basic:

    ![Выделенный код — Visual Basic](media/inline-highlight-vb.png)

1. Затем выполните одно из следующих действий:

   - **Клавиатура**
     - Нажмите клавиши **CTRL**+**.** чтобы открыть меню **Быстрые действия и рефакторинг**.
   - **Мышь**
     - Щелкните код правой кнопкой мыши и выберите меню **Быстрые действия и рефакторинг**.

1. Выберите **Встроенная временная переменная** в контекстном меню окна предварительного просмотра.

   Переменная удаляется и заменяется значением переменной.

   - C#:

    ![Встроенный результат — C#](media/inline-result-cs.png)

   - Visual Basic:

    ![Встроенный результат — Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>См. также

[Рефакторинг](../refactoring-in-visual-studio.md)