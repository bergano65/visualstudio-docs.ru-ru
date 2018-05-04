---
title: Замена временной переменной ее значением в Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: acfbfd2a23c85c81e0956190ff8e9e8501533559
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
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

- [Рефакторинг](../refactoring-in-visual-studio.md)