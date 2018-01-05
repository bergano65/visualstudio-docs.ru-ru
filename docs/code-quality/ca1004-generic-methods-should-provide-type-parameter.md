---
title: "CA1004: Универсальные методы должны предоставлять параметр типа | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4ca506d827c954a9863a6a37efd0980ecf4d8452
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: универсальные методы должны предоставлять параметр типа
|||  
|-|-|  
|TypeName|GenericMethodsShouldProvideTypeParameter|  
|CheckId|CA1004|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Сигнатура параметра универсального видимый извне метод содержит типы, которые соответствуют всех параметров типа метода.  
  
## <a name="rule-description"></a>Описание правила  
 Вывод – это то, как аргумент типа универсального метода определяется по типу аргумента, переданного методу, а не по явному указанию аргумента типа. Чтобы задействовать вывод, сигнатура параметра универсального метода должна включать параметр, тип которого совпадает с параметром типа для метода. В этом случае аргумент типа указывать не обязательно. При использовании вывода для всех параметров типа синтаксис вызова универсальных и неуниверсальных методов экземпляра является одинаковым. Это повышает удобство использования универсальных методов.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените структуру, чтобы сигнатура параметра содержит тот же тип для каждого параметра типа вызываемого метода.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует. Использование универсальных типов в синтаксисе, который легко понять и использовать, сокращает время, необходимое для обучения и ускоряет адаптацию новых библиотек.  
  
## <a name="example"></a>Пример  
 В следующем примере синтаксис вызова двух универсальных методов. Тип аргумента для `InferredTypeArgument` определяется и тип аргумента для `NotInferredTypeArgument` должна быть указана явно.  
  
 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-csharp[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1003: используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: используйте универсальные объекты, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>См. также  
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)