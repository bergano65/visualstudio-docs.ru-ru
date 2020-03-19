---
title: Завершение IntelliSense для неимпортируемых типов
description: В этой статье описывается, как использовать завершение IntelliSense для типов, которые вы еще не импортировали с помощью директивы `using`.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 04ea7c94d3dd24c1a511544adca9bfac3370cd71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094245"
---
# <a name="intellisense-completion-for-unimported-types"></a>Завершение IntelliSense для неимпортируемых типов

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** IntelliSense обеспечивает завершение для неимпортируемых типов.

**Когда?** Вы хотите добавить тип, который уже имеет зависимость в проекте, но инструкция импорта еще не добавлена в файл. 

**Зачем?** Вам не нужно будет вручную добавлять инструкцию импорта в файл.

## <a name="how-to"></a>Практические советы

1. После того как вы начнете использовать тип, который имеет зависимость в проекте, IntelliSense отобразит доступные варианты.
2. Нажмите клавишу **TAB**. 

   Инструкция импорта будет добавлена в файл.

   ![Завершение IntelliSense для неимпортируемых типов](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
