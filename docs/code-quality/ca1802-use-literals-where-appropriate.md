---
title: 'CA1802: Используйте литералы там, где возможно | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8bd2d28b7bc43c1bfa6ce941d7601b956d8f487
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802. Используйте литералы там, где возможно
|||  
|-|-|  
|TypeName|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Поле объявляется `static` и `readonly` (`Shared` и `ReadOnly` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) и инициализируется со значением, вычисляемым во время компиляции.  
  
## <a name="rule-description"></a>Описание правила  
 Значение `static``readonly` поле вычисляется во время выполнения при вызове статического конструктора для объявляющего типа. Если `static``readonly` поле инициализируется, когда он объявляется и статический конструктор не объявлен явно, компилятор выдает статический конструктор для инициализации поля.  
  
 Значение `const` поле вычисляется во время компиляции и хранится в метаданных, что повышает производительность во время выполнения, при сравнении с `static``readonly` поля.  
  
 Поскольку значение, присвоенное конечному полю, вычисляется во время компиляции, измените объявление для `const` таким образом, значение вычисляется во время компиляции, а не во время выполнения.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, замените `static` и `readonly` модификаторы с `const` модификатор.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно отключить предупреждение из этого правила, или отключить правило, если производительность не имеет значения.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип `UseReadOnly`, которое нарушает правило и тип `UseConstant`, соответствующий этому правилу.  
  
 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]