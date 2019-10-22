---
title: 'CA2231: перегрузка оператора Equals при переопределении ValueType. Equals | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 308c970eb21faa7e725559d0451706899b62fd19
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662819"
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|CheckId|CA2231|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип значения переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> но не реализует оператор равенства.

## <a name="rule-description"></a>Описание правила
 В большинстве языков программирования отсутствует стандартная реализация оператора равенства (= =) для типов значений. Если ваш язык программирования поддерживает перегрузки операторов, следует рассмотреть возможность реализации оператора равенства. Его поведение должно быть идентично поведению <xref:System.Object.Equals%2A>.

 Нельзя использовать оператор равенства по умолчанию в перегруженной реализации оператора равенства. Это приведет к переполнению стека. Чтобы реализовать оператор равенства, используйте метод Object. Equals в реализации. Пример:

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
 Чтобы устранить нарушение этого правила, реализуйте оператор равенства.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно спокойно отключить предупреждение из этого правила. Однако рекомендуется по возможности указать оператор равенства.

## <a name="example"></a>Пример
 В следующем примере определяется тип, нарушающий это правило.

 [!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EqualsGetHashCode/cs/FxCop.Usage.EqualsGetHashCode.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1046: не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: для перезагрузок оператора существуют дополнения с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: перегрузки операторов должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>См. также раздел
 <xref:System.Object.Equals%2A?displayProperty=fullName>
