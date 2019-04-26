---
title: Параметры переноса, отступа и выравнивания
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 9c17d5c9d6874c836954941e1fccd8ce9d9f2e3a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789071"
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
