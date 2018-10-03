---
title: 'CA1601: Не используйте таймеры, препятствующие изменению состояния электропитания | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: de1b5e943274b80d8a46d05dcd0cdb8fe8b2b82a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591141"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: не используйте таймеры, препятствующие изменению состояния электропитания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1601: не используйте таймеры, препятствующие изменению состояния электропитания](https://docs.microsoft.com/visualstudio/code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes).

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Категория|Microsoft.Mobility|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Таймер установлен интервал возникает несколько раз в секунду.

## <a name="rule-description"></a>Описание правила
 Не следует проводить опрос чаще, чем один раз в секунду или используйте таймеры, которые происходят чаще, чем один раз в секунду. Повышение частоты периодических действий приводит к дополнительной нагрузке на ЦП и препятствует работе таймеров энергосберегающих режимов, которые отключают монитор и жесткие диски.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Задать интервалы таймера, меньше, чем один раз в секунду.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это правило должны подавляться только в том случае, если таймер с более чем один раз в секунду, и аспекты мобильности можно спокойно проигнорировать.



