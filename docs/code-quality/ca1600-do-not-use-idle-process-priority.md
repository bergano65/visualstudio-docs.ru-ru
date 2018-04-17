---
title: 'CA1600: Не используйте приоритет процессов | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93255488efa84f553d61aaedb0474c69a4bbb8d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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