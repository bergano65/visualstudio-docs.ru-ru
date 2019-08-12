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
ms.openlocfilehash: c37affc585653807912d00c1cfe365853fd6260b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921812"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600. Не используйте приоритет процесса простоя

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Категория|Microsoft. Mobility|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Это правило происходит, когда для `ProcessPriorityClass.Idle`процессов задано значение.

## <a name="rule-description"></a>Описание правила
Не задавайте для приоритета процесса значение Idle. Процессы, которые `System.Diagnostics.ProcessPriorityClass.Idle` будут занимать ЦП, когда в противном случае они будут бездействовать, и, следовательно, блокируют ожидание.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Задайте для `ProcessPriorityClass.BelowNormal`параметра процессы значение.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Это правило следует подавлять только в том случае, если требуется приоритет процесса простоя, а вопросы мобильности можно игнорировать без каких-либо последствий.