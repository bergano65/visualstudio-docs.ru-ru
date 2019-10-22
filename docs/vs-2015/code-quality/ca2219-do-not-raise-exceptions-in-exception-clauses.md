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
ms.openlocfilehash: ebce51d360518d1cc66f652714c59d27751586b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668879"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: не создавайте исключения в предложениях исключений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое, критическое|

## <a name="cause"></a>Причина
 Исключение создается из предложения `finally`, Filter или fault.

## <a name="rule-description"></a>Описание правила
 Когда в предложении исключения возникает исключение, это значительно увеличивает сложность отладки.

 Если исключение возникает в предложении `finally` или fault, новое исключение скрывает активное исключение, если оно есть. Это делает исходную ошибку трудной для обнаружения и отладки.

 При возникновении исключения в предложении фильтра среда выполнения автоматически перехватывает исключение и приводит к тому, что фильтр возвращает значение false. Не существует способа определить разницу между фильтром, вычисляя значение false, и исключением, вызываемым из фильтра. Это затрудняет обнаружение и отладку ошибок в логике фильтра.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это нарушение в этом правиле, не вызывайте исключение явным образом из предложения `finally`, фильтра или сбоя.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение для этого правила. Не существует сценариев, в которых исключение, возникающее в предложении Exception, предоставляет преимущество для исполняемого кода.

## <a name="related-rules"></a>Связанные правила
 [CA1065: не вызывайте исключения в непредвиденных местах](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>См. также раздел
 [Предупреждения конструктора](../code-quality/design-warnings.md)
