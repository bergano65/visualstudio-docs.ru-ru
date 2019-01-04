---
title: CA2219. В предложениях с исключениями не должны порождаться исключения
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4403ab65be60000bc758cf1a127e6b589c764702
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857712"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219. В предложениях с исключениями не должны порождаться исключения

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое, критическое|

## <a name="cause"></a>Причина
 Исключение из `finally`, фильтр или предложения fault.

## <a name="rule-description"></a>Описание правила
 При возникновении исключения в предложениях исключений, значительно увеличивает сложность отладки.

 Когда возникает исключение в `finally` или предложения fault, новое исключение скрывает активное исключение, если он имеется. В результате исходную ошибку трудно обнаружить и устранить.

 При возникновении исключения в предложении filter, среда выполнения автоматически перехватывает исключение и вызывает фильтр будет сравнивать значение false. Нет способа определить разницу между фильтр имеет значение false и создает исключение фильтра исключения. Это становится трудно обнаружить и устранить ошибки в логике фильтра.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это нарушение этого правила, исключение не создается явно из `finally`, фильтр или предложения fault.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение для этого правила. Существуют не сценарии, при которых исключения, возникающие в предложении исключения предоставляет преимущество в исполняемый код.

## <a name="related-rules"></a>Связанные правила
 [CA1065: Не вызывайте исключения в непредвиденных местах](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>См. также
 [Предупреждения конструктора](../code-quality/design-warnings.md)