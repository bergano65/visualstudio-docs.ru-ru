---
title: "CA1600: Не используйте приоритет процессов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e52a658bd6161542ce909b8294f33d6e4bf140ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: не используйте приоритет процессов в состоянии ожидания
|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|Категория|Microsoft.Mobility|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Это правило возникает, если процессы `ProcessPriorityClass.Idle`.  
  
## <a name="rule-description"></a>Описание правила  
 Не задавайте для приоритета процесса значение Idle. Процессы, имеющие `System.Diagnostics.ProcessPriorityClass.Idle` будут занимать ЦП, который иначе простаивал бы, и тем самым блокировать работу standby.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Значение процессов `ProcessPriorityClass.BelowNormal`.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это правило следует отключить только в том случае, если требуется приоритет процессов и аспекты мобильности можно безопасно пропустить.