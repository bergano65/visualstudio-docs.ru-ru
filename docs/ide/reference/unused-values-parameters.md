---
title: Неиспользуемые значения и параметры
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 1ea80887fff6dcb1afba80feb782b23d1e790579
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57325029"
---
# <a name="unused-expression-values-and-parameters"></a>Неиспользуемые значения и параметры выражения

Область применения этого рефакторинга:

- C#
- Visual Basic

**Что?** Скрывает неиспользуемые параметры и создает предупреждение для неиспользуемых значений выражения.

**Когда?** У вас есть параметры и значения выражения, которые никогда не используются.

**Зачем?** Иногда бывает трудно заметить, что значение или параметр больше не используются. Если скрыть эти значения или выдать предупреждение, вы узнаете, какой код можно удалить.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Диагностика неиспользуемых значений и параметров выражения

1. Имеется значение выражения или параметра, который не используется.
2. Неиспользуемый параметр выделен неярким шрифтом. Неиспользуемое значение выражения получает предупреждение.

  ![Неиспользуемый параметр](media/unused-parameter.png)
  ![Неиспользуемое значение](media/unused-value.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Советы для разработчиков .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
