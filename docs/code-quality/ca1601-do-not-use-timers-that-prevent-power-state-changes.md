---
title: "CA1601: Не используйте таймеры, препятствующие изменению состояния электропитания | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4fb8ef82581f60cea3eb121e3d0c68fbffa82d8a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: не используйте таймеры, препятствующие изменению состояния электропитания
|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|Категория|Microsoft.Mobility|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Для таймера установлен интервал более чем один раз в секунду.  
  
## <a name="rule-description"></a>Описание правила  
 Не выполняйте опрос чаще, чем один раз в секунду, или используйте таймеры, которые происходят чаще, чем один раз в секунду. Повышение частоты периодических действий приводит к дополнительной нагрузке на ЦП и препятствует работе таймеров энергосберегающих режимов, которые отключают монитор и жесткие диски.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Задать интервалы таймера, меньше, чем один раз в секунду.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это правило следует отключить только в том случае, если таймер с более чем один раз в секунду, и вопросы энергосбережения можно игнорировать.