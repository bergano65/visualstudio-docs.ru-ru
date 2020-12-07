---
title: Упрощение условного выражения
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для упрощения условных выражений.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: dd7b3f29e804ec5e925c34f7994164d5a8465a50
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480217"
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