---
title: Преобразование оператора if в оператор switch или в выражение switch
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 93ad96809c77d5644b13e6221a41f0b182fb448f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094163"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Преобразование оператора if в оператор switch или в выражение switch

Область применения этого рефакторинга:

- C#

**Что?** Преобразование оператора if в [оператор switch](/dotnet/csharp/language-reference/keywords/switch) или в [выражение switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions) в C# 8.0.

**Когда?** Вам нужно преобразовать инструкцию `if` в инструкцию `switch` или выражение `switch` или наоборот. 

**Зачем?** Если вы используете инструкцию `if`, такой рефакторинг позволяет с легкостью выполнить переход на инструкции `switch` или выражения `switch`.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в ключевое слово `if`.
2. Нажмите клавиши **CTRL**+**.** чтобы открыть меню **Быстрые действия и рефакторинг**.
3. Выберите один из следующих двух параметров: 

    Выберите **Преобразовать в оператор switch**.

   ![Преобразование оператора if в оператор switch](media/convert-if-to-switch-statement.png) 

    Выберите **Преобразовать в выражение "switch"**. 

    ![Преобразование оператора if в выражение switch](media/convert-if-to-switch-expression.png) 

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
