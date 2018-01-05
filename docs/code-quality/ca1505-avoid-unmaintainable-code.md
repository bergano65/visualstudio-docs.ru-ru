---
title: "CA1505: Избегайте кода, неудобного для поддержки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5abaaba67d3390e36c4ad792d7b95bf41be80c2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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