---
title: CA1601. Не используйте таймеры, препятствующие изменению состояния электропитания
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1300b733cbd4808359089787ceebeb0750de6723
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234349"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601. Не используйте таймеры, препятствующие изменению состояния электропитания

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Категория|Microsoft. Mobility|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Таймер имеет интервал, настроенный на выполнение более одного раза в секунду.

## <a name="rule-description"></a>Описание правила
Не выверяйте их чаще, чем раз в секунду, или используйте таймеры, которые происходят чаще, чем один раз в секунду. Повышение частоты периодических действий приводит к дополнительной нагрузке на ЦП и препятствует работе таймеров энергосберегающих режимов, которые отключают монитор и жесткие диски.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Установите интервалы таймера, чтобы они выполнялись менее одного раза в секунду.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Это правило следует подавлять, только если требуется более одного раза в секунду, а вопросы мобильности можно пропустить.