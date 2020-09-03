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
ms.openlocfilehash: 53fa5f61cb7c503502956831452bc3eca1a9fece
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521203"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004. Удалите вызовы GC.KeepAlive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Категория|Microsoft. надежность|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Классы используют, `SafeHandle` но по-прежнему содержат вызовы `GC.KeepAlive` .

## <a name="rule-description"></a>Описание правила
 При преобразовании в `SafeHandle` Использование удалите все вызовы `GC.KeepAlive` (Object). В этом случае классы не должны вызывать метод `GC.KeepAlive` , предполагая, что они не имеют метода завершения, но используют `SafeHandle` для завершения для них маркер ОС.  Несмотря на то, что стоимость хранения в вызове `GC.KeepAlive` может быть незначительной, чем измеряется производительностью, восприятие того, что вызов `GC.KeepAlive` является обязательным или достаточным для решения проблемы времени существования, которая может быть больше не существует, затрудняет поддержание кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите вызовы к `GC.KeepAlive` .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это предупреждение можно отключить, только если технически не подходит для преобразования в `SafeHandle` использование в вашем классе.
