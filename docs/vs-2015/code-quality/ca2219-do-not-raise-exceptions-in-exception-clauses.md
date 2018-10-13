---
title: 'CA2219: Не вызывайте исключения в предложениях исключений | Документация Майкрософт'
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
ms.openlocfilehash: 32633adcff35514e8a37f409524396ec2d3f921d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49277677"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: не создавайте исключения в предложениях исключений
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
 [CA1065: не вызывайте исключения в непредвиденных местах](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>См. также
 [Предупреждения конструктора](../code-quality/design-warnings.md)



