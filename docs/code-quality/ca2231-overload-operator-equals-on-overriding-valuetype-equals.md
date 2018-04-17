---
title: 'CA2231: Перегрузка оператора равенства на переопределяющем типе ValueType.Equals | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 881b3d9761f19b4e8364f585480d8b055d076a38
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals
|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|  
|CheckId|CA2231|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Тип значения переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> , но не реализует оператор равенства.  
  
## <a name="rule-description"></a>Описание правила  
 В большинстве языков программирования отсутствует реализация по умолчанию для типов значений оператора равенства (==). Если язык программирования поддерживает перегрузки операторов, следует рассмотреть, реализации оператора равенства. Его поведение должно быть идентично <xref:System.Object.Equals%2A>.  
  
 Оператор проверки на равенство по умолчанию нельзя использовать в перегруженной реализации оператора равенства. Это приведет к переполнению стека. Чтобы реализовать оператор равенства, используйте метод Object.Equals в реализации. Пример:  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```csharp  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, реализуйте оператор равенства.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила; Тем не менее Корпорация Майкрософт рекомендует по возможности укажите оператор равенства.  
  
## <a name="example"></a>Пример  
 В следующем примере определяется тип, нарушающий это правило.  
  
 [!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../code-quality/codesnippet/CSharp/ca2231-overload-operator-equals-on-overriding-valuetype-equals_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1046: не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: для перезагрузок оператора существуют дополнения с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: перегрузки операторов должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.Object.Equals%2A?displayProperty=fullName>