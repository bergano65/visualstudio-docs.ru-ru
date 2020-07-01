---
title: Завершение DateTime и TimeSpan через меню IntelliSense
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: eaa8a344e46c031b37b52106ba9aef25dac59b0c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290910"
---
# <a name="datetime-and-timespan-completion-through-intellisense-menu"></a>Завершение DateTime и TimeSpan через меню IntelliSense

Область применения этого рефакторинга:

- C#

**Что?** Завершение строковых литералов DateTime и TimeSpan через меню IntelliSense.

**Когда?** Вам нужно написать строковые литералы DateTime и TimeSpan. IntelliSense выполнит базовое завершение и предоставит пояснение того, что значит каждый символ. 

**Зачем?** Запомнить форматы DateTime может быть непросто, и IntelliSense поможет вам.

## <a name="how-to"></a>Практические советы

1. Поместите курсор на строковый литерал DateTime или TimeSpan.
2. Нажмите клавиши **Ctrl**+**Пробел**, чтобы открыть меню **IntelliSense**.
3. Выберите символ, который вы хотите добавить.

   ![Завершение DateTime с помощью IntelliSense](media/datetime-completion.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
