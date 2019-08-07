---
title: Преобразование инструкции switch в выражение switch
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cc13cffe8352d9fb57f5bb991c3af615eddb2a14
ms.sourcegitcommit: b56dc6fadc6c924beed36bb4c2ccc16cf6bcfa1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2019
ms.locfileid: "68740062"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Преобразование инструкции switch в выражение switch

Область применения этого рефакторинга:

- C#

**Что?** Преобразование [инструкции switch](/dotnet/csharp/language-reference/keywords/switch) в [выражение switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions) для языка C# 8.0.

**Когда?** Вам нужно преобразовать инструкцию `switch` в выражение `switch` или наоборот. 

**Зачем?** Если вы используете только выражения, такой рефакторинг позволяет с легкостью выполнить переход от традиционных инструкций `switch`.

## <a name="how-to"></a>Практические советы

1. В файле проекта [выберите предварительную версию для версии языка](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file),так как выражения `switch` — это новая возможность C# 8.0.
2. Поместите курсор в ключевое слово `switch` и нажмите клавиши **Ctrl**+ **.** , чтобы открыть меню **Быстрые действия и рефакторинг**.
3. Выберите **Преобразовать инструкцию switch в выражение**.

   ![Преобразование инструкции switch в выражение switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
