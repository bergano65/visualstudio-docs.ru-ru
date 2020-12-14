---
title: Инверсия условных выражений и логических операций
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для инвертирования условных выражений или условных операторов И/ИЛИ.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 180e42d5399116df95289e4e5fd0aed1255bf3de
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617387"
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

    ![Снимок экрана: параметр "Инвертировать условный оператор".](media/invert-conditional.png)

    ![Снимок экрана: параметр "Заменить && на ||".](media/invert-logical-operator.png)

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Советы для разработчиков .NET](../csharp-developer-productivity.md)
