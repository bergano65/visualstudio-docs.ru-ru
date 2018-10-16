---
title: 'CA2004: Удалите вызовы GC. KeepAlive | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e9d7e9a833c71145b97b4f9c0e979e6e415b6628
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182043"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: удалите вызовы GC.KeepAlive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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



