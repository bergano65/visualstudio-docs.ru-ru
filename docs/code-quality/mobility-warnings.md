---
title: "Предупреждения мобильности | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.MobilityRules"
helpviewer_keywords: 
  - "предупреждения при анализе управляемого кода, предупреждения мобильности"
  - "предупреждения мобильности"
  - "предупреждения, мобильность"
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# Предупреждения мобильности
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Предупреждения мобильности поддерживают эффективное энергопотребление.  
  
## В этом подразделе  
  
|Правило|Описание|  
|-------------|--------------|  
|[CA1600: не используйте приоритет процессов в состоянии ожидания](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Не задавайте для приоритета процесса значение Idle.  Процессы с приоритетом System.Diagnostics.ProcessPriorityClass.Idle будут занимать ЦП, который иначе простаивал бы, и тем самым блокировать работу в режиме ожидания.|  
|[CA1601: не используйте таймеры, препятствующие изменению состояния электропитания](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Повышение частоты периодических действий приводит к дополнительной нагрузке на ЦП и препятствует работе таймеров энергосберегающих режимов, которые отключают монитор и жесткие диски.|