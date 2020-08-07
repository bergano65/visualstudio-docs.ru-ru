---
title: Завершение DateTime и TimeSpan через меню IntelliSense
ms.date: 07/31/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 36b6d5440e532653845638f87f7f1d7066af6ba3
ms.sourcegitcommit: 43df639b2cd99200f725a8ebb941477481a6f0ff
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/31/2020
ms.locfileid: "87471561"
---
# <a name="datetime-and-timespan-completion-through-intellisense-menu"></a>Завершение DateTime и TimeSpan через меню IntelliSense

Область применения этого рефакторинга:

- C#

**Что?** Завершение строковых литералов DateTime и TimeSpan, а также строк формата через меню IntelliSense.

**Когда?** Вам нужно написать строковые литералы DateTime и TimeSpan, а также строки формата. IntelliSense выполнит базовое завершение и предоставит пояснение того, что значит каждый символ. 

**Зачем?** Запомнить форматы DateTime может быть непросто, и IntelliSense поможет вам.

## <a name="how-to"></a>Практические советы

1. Поместите курсор на строку формата DateTime или TimeSpan.
2. Нажмите клавиши **Ctrl**+**Пробел**, чтобы открыть меню **IntelliSense**.
3. Выберите символ, который вы хотите добавить.

   ![Завершение DateTime с помощью IntelliSense](media/datetime-completion.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
