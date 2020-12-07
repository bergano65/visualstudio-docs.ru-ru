---
title: Преобразование инструкции switch в выражение switch
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для преобразования инструкции switch в выражение switch C# 8.0.
ms.custom: SEO-VS-2020
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: add43010fcec04cbe12889672f561f22057efb8c
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305519"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Преобразование инструкции switch в выражение switch

Область применения этого рефакторинга:

- C#

**Что?** Преобразование [инструкции switch](/dotnet/csharp/language-reference/keywords/switch) в [выражение switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions) для языка C# 8.0.

**Когда?** Вам нужно преобразовать инструкцию `switch` в выражение `switch` или наоборот. 

**Зачем?** Если вы используете только выражения, такой рефакторинг позволяет с легкостью выполнить переход от традиционных инструкций `switch`.

## <a name="how-to"></a>Практическое руководство

1. В файле проекта [выберите предварительную версию для версии языка](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file),так как выражения `switch` — это новая возможность C# 8.0.
2. Поместите курсор в ключевое слово `switch` и нажмите клавиши **Ctrl**+ **.** , чтобы открыть меню **Быстрые действия и рефакторинг**.
3. Выберите **Преобразовать инструкцию switch в выражение**.

   ![Преобразование инструкции switch в выражение switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
