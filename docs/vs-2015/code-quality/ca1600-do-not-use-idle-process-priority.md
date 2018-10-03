---
title: 'CA1600: Не используйте приоритет процессов | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: b211c1ab646d27cf32290d3c5c306719ba7decff
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592081"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: не используйте приоритет процессов в состоянии ожидания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1600: не используйте приоритет процессов](https://docs.microsoft.com/visualstudio/code-quality/ca1600-do-not-use-idle-process-priority).

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



