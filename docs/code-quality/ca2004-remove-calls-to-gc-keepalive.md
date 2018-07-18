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
ms.openlocfilehash: fa59c6797d81202637f44799327e6b2802d822eb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917193"
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