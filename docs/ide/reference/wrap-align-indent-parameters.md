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
ms.openlocfilehash: ccdf29e3a4cda2bf5d527a2b712878c1fbd76197
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2019
ms.locfileid: "66037583"
---
# <a name="wrap-indent-and-align-parameters-or-arguments"></a>Аргументы или параметры переноса, отступа и выравнивания

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Обеспечивает параметры или аргументы переноса, отступа и выравнивания.

**Когда?** У вас есть объявление метода или вызов, который имеет несколько параметров или аргументов.

**Зачем?** Читать длинный список параметров или аргументов будет проще, если используется перенос или отступ в соответствии с предпочтениями пользователя.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в список параметров.
2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

   ![Параметры переноса, отступа и выравнивания](media/wrap-parameters.png)

3. Нажмите клавишу **ВВОД**, чтобы принять рефакторинг.

   ![Параметры переноса, отступа и выравнивания применены](media/wrap-parameters-completed.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
