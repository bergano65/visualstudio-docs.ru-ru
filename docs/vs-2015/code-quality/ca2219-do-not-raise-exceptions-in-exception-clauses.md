---
title: 'CA2219: не вызывайте исключения в предложениях исключений | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 960c74625a04b209dc9aa251256e994517a3a52f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538532"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219. В предложениях с исключениями не должны порождаться исключения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое, критическое|

## <a name="cause"></a>Причина
 Исключение создается из `finally` предложения, фильтра или сбоя.

## <a name="rule-description"></a>Описание правила
 Когда в предложении исключения возникает исключение, это значительно увеличивает сложность отладки.

 Если исключение возникает в `finally` предложении или, новое исключение скрывает активное исключение, если оно есть. Это делает исходную ошибку трудной для обнаружения и отладки.

 При возникновении исключения в предложении фильтра среда выполнения автоматически перехватывает исключение и приводит к тому, что фильтр возвращает значение false. Не существует способа определить разницу между фильтром, вычисляя значение false, и исключением, вызываемым из фильтра. Это затрудняет обнаружение и отладку ошибок в логике фильтра.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это нарушение в этом правиле, не вызывайте исключение явным образом из `finally` предложения, фильтра или сбоя.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение для этого правила. Не существует сценариев, в которых исключение, возникающее в предложении Exception, предоставляет преимущество для исполняемого кода.

## <a name="related-rules"></a>Связанные правила
 [CA1065. Не вызывайте исключения в непредвиденных местах](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>См. также
 [Предупреждения конструктора](../code-quality/design-warnings.md)
