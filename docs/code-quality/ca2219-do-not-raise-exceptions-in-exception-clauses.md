---
title: 'CA2219: Не вызывайте исключения в предложениях исключений | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: abe5fe25297c61e84e19857747c19b3602f78e0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: не создавайте исключения в предложениях исключений
|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInExceptionClauses|  
|CheckId|CA2219|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое, критическое|  
  
## <a name="cause"></a>Причина  
 Порождено исключение `finally`, фильтр или предложения fault.  
  
## <a name="rule-description"></a>Описание правила  
 При возникновении исключения в предложениях исключений значительно увеличивает сложность отладки.  
  
 Если исключение создается в `finally` или fault, новое исключение скрывает активное исключение, при его наличии. Это становится трудно обнаружить и отладить изначальную ошибку.  
  
 Исключение создается в предложении filter, среда выполнения автоматически перехватывает исключение и фильтр возвращает значение false. Нет, чтобы определить разницу между фильтр имеет значение false, а также создает исключение фильтра исключения. Это становится трудно обнаружить и отладить ошибки в логике фильтра.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, исключение не создается явным образом из `finally`, фильтр или предложения fault.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте предупреждение для этого правила. Нет ни в каких случаях, в которых исключение, созданное в предложении исключения предоставляет преимущество в исполняемый код.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1065: не вызывайте исключения в непредвиденных местах](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)  
  
## <a name="see-also"></a>См. также  
 [Предупреждения конструктора](../code-quality/design-warnings.md)