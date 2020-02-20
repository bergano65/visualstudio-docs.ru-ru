---
title: Преобразование оператора if в оператор switch или в выражение switch
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cb0c06fe0493f973ea9cf0a566ffda45a49eeeff
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2020
ms.locfileid: "77283463"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Преобразование оператора if в оператор switch или в выражение switch

Область применения этого рефакторинга:

- C#

**Что?** Преобразование оператора if в [оператор switch](/dotnet/csharp/language-reference/keywords/switch) или в [выражение switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions) в C# 8.0.

**Когда?** Вам нужно преобразовать инструкцию `if` в инструкцию `switch` или выражение `switch` или наоборот. 

**Зачем?** Если вы используете инструкцию `if`, такой рефакторинг позволяет с легкостью выполнить переход на инструкции `switch` или выражения `switch`.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в ключевое слово `if`.
2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.
3. Выберите **Преобразовать в оператор switch**.

   ![Преобразование оператора if в оператор switch или в выражение switch](media/convert-if-statement-to-switch-statement-or-switch-expression.png) 

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
