---
title: 'CA2004: удалите вызовы GC.KeepAlive'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bea4af6c0ae0e21e15a79d52f4c7205a51a3ea46
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819125"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: удалите вызовы GC.KeepAlive

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