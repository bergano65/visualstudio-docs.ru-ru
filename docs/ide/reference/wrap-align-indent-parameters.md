---
title: Параметры переноса, отступа и выравнивания
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 1490ff0bcae91a6f4870b0cfb623d975fa1e064b
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335887"
---
# <a name="wrap-indent-and-align-parameters"></a>Параметры переноса, отступа и выравнивания

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Обеспечивает параметры переноса, отступа и выравнивания.

**Когда?** У вас есть объявление метода или вызов, который имеет несколько параметров.

**Зачем?** Читать длинный список параметров будет проще, если используется перенос или отступ в соответствии с предпочтениями пользователя.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в список параметров.
2. Нажмите клавиши **CTRL**+**.** чтобы открыть меню **Быстрые действия и рефакторинг**.

   ![Параметры переноса, отступа и выравнивания](media/wrap-parameters.png)

3. Нажмите клавишу **ВВОД**, чтобы принять рефакторинг.

   ![Параметры переноса, отступа и выравнивания применены](media/wrap-parameters-completed.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
