---
title: 'CA1601: не используйте таймеры, препятствующие изменению состояния электропитания | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 95f13604908ad45c5f33a011fec886bba90d0bd8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669276"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: не используйте таймеры, препятствующие изменению состояния электропитания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Категория|Microsoft. Mobility|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Таймер имеет интервал, настроенный на выполнение более одного раза в секунду.

## <a name="rule-description"></a>Описание правила
 Не выверяйте их чаще, чем раз в секунду, или используйте таймеры, которые происходят чаще, чем один раз в секунду. Повышение частоты периодических действий приводит к дополнительной нагрузке на ЦП и препятствует работе таймеров энергосберегающих режимов, которые отключают монитор и жесткие диски.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Установите интервалы таймера, чтобы они выполнялись менее одного раза в секунду.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это правило следует подавлять, только если требуется более одного раза в секунду, а вопросы мобильности можно пропустить.
