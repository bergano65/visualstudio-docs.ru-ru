---
title: Упрощение условного выражения
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для упрощения условных выражений.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: fc05aa1026560f91f9a31080ace0b2c9c9319357
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957573"
---
# <a name="simplify-conditional-expression-refactoring"></a>Упрощение рефакторинга условных выражений:

Область применения этого рефакторинга:

- C#

**Что?** Вы можете упростить [условное выражение](/dotnet/csharp/language-reference/operators/conditional-operator).

**Когда?** Если необходимо удалить ненужный код для большей ясности.

**Зачем?** Упрощение условного выражения может обеспечить более наглядный и краткий синтаксис. Это средство рефакторинга выполнит указанную задачу автоматически, и вам не придется делать это вручную.

## <a name="how-to"></a>Практические советы

1. Установите курсор в условном выражении.

2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

3. Выберите **Упростить условное выражение**.

    ![Упрощение условного выражения](media/simplify-conditional-expression.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)