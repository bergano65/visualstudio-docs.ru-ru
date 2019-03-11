---
title: Инверсия условных выражений и логических операций
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a35f5949bee6cb3c4fbcbf9ba6a9b501d54b2014
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324589"
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
2. Нажмите клавиши **CTRL**+**.** чтобы открыть меню **Быстрые действия и рефакторинг**.
3. Выберите **Инвертировать условия** или **Заменить && на ||**

    ![Инвертировать условия](media/invert-conditional.png)

    ![Инвертировать условия](media/invert-logical-operator.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Советы для разработчиков .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
