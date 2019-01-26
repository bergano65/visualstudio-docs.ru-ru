---
title: CA2004. Удалите вызовы GC.KeepAlive
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 2e2787b3d0876034113e777d7f8932d63e5c1a27
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001463"
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