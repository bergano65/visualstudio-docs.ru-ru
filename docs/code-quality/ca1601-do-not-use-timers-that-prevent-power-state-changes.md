---
title: "CA1601: не используйте таймеры, препятствующие изменению состояния электропитания | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
helpviewer_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1601: не используйте таймеры, препятствующие изменению состояния электропитания
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|Категория|Microsoft.Mobility|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Для таймера установлен интервал меньше одной секунды.  
  
## Описание правила  
 Не следует проводить опрос чаще, чем один раз в секунду, или использовать таймеры, интервал которых меньше секунды.  Повышение частоты периодических действий приводит к дополнительной нагрузке на ЦП и препятствует работе таймеров энергосберегающих режимов, которые отключают монитор и жесткие диски.  
  
## Устранение нарушений  
 Установите для таймеров интервалы, превышающие одну секунду.  
  
## Отключение предупреждений  
 Данное правило следует отключать только в том случае, если требуется срабатывание таймера с интервалом меньше одной секунды и можно пренебречь соображениями мобильности без серьезных последствий.