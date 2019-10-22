---
title: 'CA1600: не использовать приоритет процесса простоя | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d4260db808d9c50f78388cf6ba976f7ace52e6a3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669296"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: не используйте приоритет процессов в состоянии ожидания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Категория|Microsoft. Mobility|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Это правило возникает, когда для процессов задано значение `ProcessPriorityClass.Idle`.

## <a name="rule-description"></a>Описание правила
 Не задавайте для приоритета процесса значение Idle. Процессы, имеющие `System.Diagnostics.ProcessPriorityClass.Idle`, будут занимать ЦП, когда в противном случае он будет бездействовать, и поэтому будет блокировать ждущий режим.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Задайте для процессов `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это правило следует подавлять только в том случае, если требуется приоритет процесса простоя, а вопросы мобильности можно игнорировать без каких-либо последствий.
