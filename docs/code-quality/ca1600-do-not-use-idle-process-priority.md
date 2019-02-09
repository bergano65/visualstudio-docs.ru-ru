---
title: CA1600. Не используйте приоритет процесса простоя
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1774b3feb2da4939420bf75506892aac6dedd72
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955795"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600. Не используйте приоритет процесса простоя

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Категория|Microsoft.Mobility|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Это правило возникает, если процессы `ProcessPriorityClass.Idle`.

## <a name="rule-description"></a>Описание правила
 Не задавайте для приоритета процесса значение Idle. Процессы, имеющие `System.Diagnostics.ProcessPriorityClass.Idle` будут занимать ЦП, когда он иначе простаивал бы и тем самым блокировать работу standby.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Значение процессов `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это правило должны подавляться только в том случае, если требуется приоритет процессов и аспекты мобильности можно безопасно проигнорировать.