---
title: Как сделать элемент статическим
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1ecc66cb58ad11bd431acb341dae0493ce8192da
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "77519305"
---
# <a name="make-member-static"></a>Как сделать элемент статическим

Область применения этого рефакторинга:

- C#

**Что?** Преобразование элемента в статический.

**Когда?** Вы хотите сделать нестатический элемент статическим.

**Зачем?** Статические элементы обеспечивают удобочитаемость: благодаря изоляции конкретного кода его проще разобрать, прочесть повторно и повторно использовать. 

## <a name="how-to"></a>Практические советы

1. Поместите курсор на имя элемента.

2. Нажмите клавиши **CTRL**+ **.** (точка), чтобы открыть меню **Quick Actions and Refactorings** (Быстрые действия и рефакторинг).

   ![Как сделать элемент статическим](media/make-member-static.png)

3. Выберите **Сделать статическим**.

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
