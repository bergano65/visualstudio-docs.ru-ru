---
title: CA2004. Удалите вызовы GC.KeepAlive
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4520649050e6e4004b2c8864d5c081897852826c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808370"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004. Удалите вызовы GC.KeepAlive

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Категория|Microsoft.Reliability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Классы используют `SafeHandle` , но по-прежнему содержать вызовы `GC.KeepAlive`.

## <a name="rule-description"></a>Описание правила
 При переходе к `SafeHandle` использование, удалить все вызовы `GC.KeepAlive` (объект). Классы в этом случае не следует вызывать `GC.KeepAlive`, при условии, что они не имеют метод завершения, а на `SafeHandle` для завершения дескриптора ОС для них.  Несмотря на то что затраты на оставшиеся в вызове `GC.KeepAlive` может быть совсем незаметной, измеренной по производительности, восприятие, вызов `GC.KeepAlive` необходим или достаточен для решения времени существования, проблема, которая больше не существует делает код труднее Ведение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите вызовы `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это предупреждение можно отключить только в том случае, если это не технической точки зрения правильно для преобразования в `SafeHandle` использования в вашем классе.