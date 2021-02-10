---
title: Преобразование инструкции switch в выражение switch
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для преобразования инструкции switch в выражение switch C# 8.0.
ms.custom: SEO-VS-2020
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 56a1b20854cdd2c1821490bb4972d67bbe912056
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919670"
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
