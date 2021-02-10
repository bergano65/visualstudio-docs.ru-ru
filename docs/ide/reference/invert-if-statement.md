---
title: Инверсия инструкции if
description: Узнайте, как с помощью меню "Быстрые действия и рефакторинг" инвертировать инструкцию If или if else, не изменяя значение кода.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cf4ad7c25030e4a331ee67f4957ddac59afdd966
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852236"
---
# <a name="invert-if-statement"></a>Инверсия инструкции if

Область применения этого рефакторинга:

- C#
- Visual Basic

**Что?** Позволяет инвертировать инструкцию `if` или `if else`, не изменяя значение кода.

**Когда?** При наличии инструкции `if` или `if else`, которая будет понятнее после инверсии.

**Зачем?** Инверсия инструкции `if` или `if else` вручную может занять гораздо больше времени и привести к ошибкам. Это исправление кода помогает выполнять рефакторинг автоматически.

## <a name="invert-if-statement-refactoring"></a>Рефакторинг "Инверсия инструкции if"

1. Поместите курсор в инструкции `if` или `if else`.

    ![Инверсия if else](media/invert-if.png)

2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

    ![Исправление "Инверсия if else"](media/invert-if-codefix.png)

3. Выберите **Инвертировать if**.

    ![Результат инверсии if else](media/invert-if-codefix-result.png)

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Советы для разработчиков .NET](../csharp-developer-productivity.md)
