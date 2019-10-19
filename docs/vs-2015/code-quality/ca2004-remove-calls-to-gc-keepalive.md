---
title: 'CA2004: удаление вызовов GC. KeepAlive | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e34a8e7d4860a599155554410e13df5a6eb3bfe1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672494"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: удалите вызовы GC.KeepAlive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Категория|Microsoft. надежность|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Классы используют `SafeHandle`, но по-прежнему содержат вызовы `GC.KeepAlive`.

## <a name="rule-description"></a>Описание правила
 При преобразовании в `SafeHandle` использование удалите все вызовы `GC.KeepAlive` (Object). В этом случае классы не должны вызывать `GC.KeepAlive`, предполагая, что они не имеют метода завершения, но полагаются на `SafeHandle` для завершения работы с маркерами ОС.  Несмотря на то, что стоимость хранения в вызове `GC.KeepAlive` может быть незначительной, чем измеряется производительностью, восприятие того, что вызов `GC.KeepAlive` является необходимым или достаточным для решения проблемы времени существования, которая, возможно, больше не существует, усложняет поддержание кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите вызовы к `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это предупреждение можно отключить, только если технически не подходит для преобразования в `SafeHandle` использования в классе.
