---
title: Инверсия условных выражений и логических операций
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3931ae53fc29b0ffd8b8b6e96951a0f4786ff756
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531678"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Инверсия условных выражений и условных операторов И/ИЛИ

Область применения этого рефакторинга:

- C#
- Visual Basic

**Что?** Позволяет инвертировать условные выражения и условные операторы И/ИЛИ.

**Когда?** У вас есть условное выражение или условный оператор И/ИЛИ, который будет более понятен после инверсии.

**Зачем?** Инверсия выражения или условного оператора И/ИЛИ вручную может занимать гораздо больше времени и приводить к ошибкам. Это исправление кода помогает выполнять рефакторинг автоматически.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Рефакторинг "Инверсия условных выражений и условных операторов И/ИЛИ"

1. Поместите курсор в условное выражение или условный оператор И/ИЛИ.
2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.
3. Выберите **Инвертировать условия** или **Заменить && на ||**

    ![Инвертировать условия](media/invert-conditional.png)

    ![Инвертировать условия](media/invert-logical-operator.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Советы для разработчиков .NET](../csharp-developer-productivity.md)
