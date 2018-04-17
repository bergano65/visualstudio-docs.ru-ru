---
title: 'CA1505: Избегайте кода, неудобного для поддержки | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4338b73aab38b1d63f4d4015c3a1fe1e1d292932
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505. Избегайте кода, неудобного для поддержки
|||  
|-|-|  
|TypeName|AvoidUnmantainableCode|  
|CheckId|CA1505|  
|Категория|Microsoft.Maintainability|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Тип или метод имеет низкий индекс обслуживаемости.  
  
## <a name="rule-description"></a>Описание правила  
 Индекс удобства поддержки вычисляется с помощью следующих метрик: строки кода, объем программы и сложность. Программа тома — это мера трудности понимания типа или метод, основанный на количестве операторов и операндов в коде. Сложность — это мера сложности структурного типа или метода. Дополнительные сведения о метриках кода в [Оценка сложности и удобства поддержки управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).  
  
 Низкий индекс обслуживаемости указывает, что тип или метод, вероятно, трудно поддерживать и будет хорошим кандидатом для переработки.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Для устранения нарушения данного правила, измените тип или метод и попробуйте разделить ее на более мелкие и более конкретные типы или методы.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Исключите это предупреждение, когда тип или метод считается обслуживаемым несмотря на крупный размер, или когда тип или метод не может быть разбит.  
  
## <a name="see-also"></a>См. также  
 [Предупреждения удобства обслуживания](../code-quality/maintainability-warnings.md)   
 [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)