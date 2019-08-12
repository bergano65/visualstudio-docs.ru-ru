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
ms.openlocfilehash: a716da8eb0fb1b741c302ed32408e63a4933567b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921140"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004. Удалите вызовы GC.KeepAlive

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Категория|Microsoft. надежность|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Классы используют `SafeHandle` , но по-прежнему `GC.KeepAlive`содержат вызовы.

## <a name="rule-description"></a>Описание правила
При преобразовании в `SafeHandle` использование удалите все `GC.KeepAlive` вызовы (Object). В этом случае классы не должны вызывать метод `GC.KeepAlive`, предполагая, что они не имеют метода завершения, но `SafeHandle` используют для завершения для них маркер ОС.  Несмотря на то, что затраты на уход в `GC.KeepAlive` вызове могут быть незаметны, как и в случае с производительностью, восприятие того, что `GC.KeepAlive` вызов является обязательным или достаточным для решения проблемы времени существования, которая может больше не существовать, усложняет код обеспечивать.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Удалите вызовы к `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Это предупреждение можно отключить, только если технически не подходит для преобразования `SafeHandle` в использование в вашем классе.