---
title: 'CA2004: Удалите вызовы GC. KeepAlive | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d25c42202f7df2214295af4e3d1a448266cfa6cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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