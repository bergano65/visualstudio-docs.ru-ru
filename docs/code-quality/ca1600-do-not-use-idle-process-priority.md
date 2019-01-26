---
title: CA1600. Не используйте приоритет процесса простоя
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: f9eb25ace4ee255348f616abefcccd84713715ff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037529"
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