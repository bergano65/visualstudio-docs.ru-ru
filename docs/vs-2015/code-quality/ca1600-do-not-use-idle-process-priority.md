---
title: CA1600. Не используйте приоритет процессов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4002e17e3988ca3b449e141394ce762f95ffc78b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189298"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600. Не используйте приоритет процесса простоя
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
