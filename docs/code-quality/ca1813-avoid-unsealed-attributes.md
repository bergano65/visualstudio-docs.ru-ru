---
title: 'CA1813: Не распечатанных атрибутов | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04f557dea4fca796de4e786737f7cef2b59a3896
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: не допускайте использования распечатанных атрибутов
|||  
|-|-|  
|TypeName|AvoidUnsealedAttributes|  
|CheckId|CA1813|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый тип наследует от <xref:System.Attribute?displayProperty=fullName>, не является абстрактным и не является запечатанным (`NotInheritable` в Visual Basic).  
  
## <a name="rule-description"></a>Описание правила  
 В библиотеке классов [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] предоставляются методы для извлечения пользовательских атрибутов. По умолчанию эти методы осуществляют поиск иерархии наследования атрибутов; например <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> ищет указанный тип атрибута или любой тип атрибута, который расширяет тип указанного атрибута. Если запечатать атрибут устраняет поиск иерархии наследования и может повысить производительность.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, запечатайте атрибут или сделайте его абстрактным.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Его можно безопасно подавить предупреждение из этого правила. Это необходимо только в том случае, если иерархия атрибута определяется и запечатать атрибут или нельзя сделать абстрактным.  
  
## <a name="example"></a>Пример  
 В следующем примере показано пользовательский атрибут, который соответствует данному правилу.  
  
 [!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1019: необходимо определять методы доступа для аргументов атрибутов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018: помечайте атрибуты как AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## <a name="see-also"></a>См. также  
 [Атрибуты](/dotnet/standard/design-guidelines/attributes)