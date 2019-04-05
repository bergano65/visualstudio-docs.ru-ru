---
title: CA2219. Не вызывайте исключения в предложениях исключений | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 506b9d243ef83242b7e17c295dfc13ef9039d1f6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978699"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219. В предложениях с исключениями не должны порождаться исключения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
