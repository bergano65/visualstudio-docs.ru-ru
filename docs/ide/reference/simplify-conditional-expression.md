---
title: Упрощение условного выражения
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 0242c8c89848e3e76673ddfbca8a27c20605048d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810354"
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