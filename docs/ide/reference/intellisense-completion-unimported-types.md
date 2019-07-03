---
title: Завершение IntelliSense для неимпортируемых типов
description: В этой статье описывается, как использовать завершение IntelliSense для типов, которые вы еще не импортировали с помощью директивы `using`.
ms.date: 06/20/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f313cfa8520e4c13b310be0f9223466c529ca18f
ms.sourcegitcommit: 16bcaca215de75479695738d3c2d703c78c3500e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/21/2019
ms.locfileid: "67312913"
---
# <a name="intellisense-completion-for-unimported-types"></a>Завершение IntelliSense для неимпортируемых типов

Область применения этого рефакторинга:

- C#

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
