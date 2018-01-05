---
title: "CA2004: Удалите вызовы GC. KeepAlive | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dd6cc8b51ddd8f9e8813229cf66b9facb52e4668
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: удалите вызовы GC.KeepAlive
|||  
|-|-|  
|TypeName|RemoveCallsToGCKeepAlive|  
|CheckId|CA2004|  
|Категория|Microsoft.Reliability|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Классы используют `SafeHandle` , но по-прежнему содержат вызовы `GC.KeepAlive`.  
  
## <a name="rule-description"></a>Описание правила  
 При преобразовании к `SafeHandle` использование, удалить все вызовы `GC.KeepAlive` (объект). В этом случае классам не требуется вызывать `GC.KeepAlive`, при условии, что они не имеют метод завершения, а на `SafeHandle` для завершения дескриптора ОС для них.  Хотя затраты на оставшиеся в вызове `GC.KeepAlive` может оказаться незначительной по производительности, понимание того, вызов `GC.KeepAlive` является необходимым или достаточно решить проблему, которая больше не существует делает код труднее время существования Ведение.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Удалите вызов `GC.KeepAlive`.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это предупреждение можно отключить только в том случае, если это не технически правильно будет преобразовать в `SafeHandle` использование в классе.