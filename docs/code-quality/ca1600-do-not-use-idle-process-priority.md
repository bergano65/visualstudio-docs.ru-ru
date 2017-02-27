---
title: "CA1600: не используйте приоритет процессов в состоянии ожидания | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotUseIdleProcessPriority"
  - "CA1600"
helpviewer_keywords: 
  - "CA1600"
  - "DoNotUseIdleProcessPriority"
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1600: не используйте приоритет процессов в состоянии ожидания
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|Категория|Microsoft.Mobility|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Данное правило срабатывает, когда процессам задается `ProcessPriorityClass.Idle`.  
  
## Описание правила  
 Не задавайте для приоритета процесса значение Idle.  Процессы с приоритетом `System.Diagnostics.ProcessPriorityClass.Idle` будут занимать ЦП, который иначе простаивал бы, и тем самым блокировать работу в режиме ожидания.  
  
## Устранение нарушений  
 Установите для процессов приоритет `ProcessPriorityClass.BelowNormal`.  
  
## Отключение предупреждений  
 Данное правило следует отключать только в том случае, если требуется использовать приоритет процесса бездействия и можно пренебречь соображениями мобильности без серьезных последствий.