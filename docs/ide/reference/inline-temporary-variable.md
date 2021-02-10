---
title: Замена временной переменной ее значением
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для удаления временной переменной и ее замены значением.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ebe062d5dd569ae1d2162ea7334f91d8b82decdb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852379"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Рефакторинг для замены временной переменной

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Удаление временной переменной и ее замена значением.

**Когда?** Использование временной переменной затрудняет понимание кода.

**Зачем?** Удаление временной переменной может сделать код более удобным для чтения.

## <a name="how-to"></a>Практические советы

1. Выделите временную переменную или наведите на нее курсор для замены:

   - C#:

       ![Выделенный код — C#](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Выделенный код — Visual Basic](media/inline-highlight-vb.png)

2. Затем выполните одно из следующих действий.

   - **Клавиатура**
      - Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.
   - **Мышь**
      - Щелкните код правой кнопкой мыши и выберите меню **Быстрые действия и рефакторинг**.

3. Выберите **Встроенная временная переменная** в контекстном меню окна предварительного просмотра.

   Переменная удаляется и заменяется значением переменной.

   - C#:

      ![Встроенный результат — C#](media/inline-result-cs.png)

   - Visual Basic:

      ![Встроенный результат — Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
