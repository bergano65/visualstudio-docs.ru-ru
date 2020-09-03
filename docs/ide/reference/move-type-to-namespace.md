---
title: Перемещение типа в пространство имен
ms.date: 06/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
monikerRange: vs-2019
ms.openlocfilehash: 58d2757fa8798b67c8e597f5f82bc65a279f4a90
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80375571"
---
# <a name="move-type-to-namespace"></a>Перемещение типа в пространство имен

Область применения этого рефакторинга:

- C#

**Что?** Перемещение типа в пространство имен.

**Когда?** Вам нужно переместить тип в другое пространство имен или папку. 

**Зачем?** Вы хотите выполнить рефакторинг частей своего решения и таким образом сможете быстро переместить тип в другое пространство имен или папку. 

## <a name="how-to"></a>Практические советы

1. Поместите курсор в имени класса.
2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.
3. Выберите **Переместить в пространство имен**.

   ![Рефакторинг с перемещением в пространство имен](media/move-to-namespace.png)

4. В открывшемся диалоговом окне выберите целевое пространство имен, в которое нужно переместить тип. 

   ![Диалоговое окно с выбором пространства имен](media/select-target-namespace.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
