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
ms.openlocfilehash: f01495e4238461d0b1dfe5a13a208b528df1581f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540300"
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231. Перегрузите оператор равенства на переопределяющем типе ValueType.Equals
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|CheckId|CA2231|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип значения переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> , но не реализует оператор равенства.

## <a name="rule-description"></a>Описание правила
 В большинстве языков программирования отсутствует стандартная реализация оператора равенства (= =) для типов значений. Если ваш язык программирования поддерживает перегрузки операторов, следует рассмотреть возможность реализации оператора равенства. Его поведение должно быть идентично его поведению <xref:System.Object.Equals%2A> .

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
 [CA1046. Не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225. Для перегрузок операторов существуют варианты с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226. Перегрузки операторов должны быть симметричными](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224. Переопределяйте Equals при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218. Переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>См. также:
 <xref:System.Object.Equals%2A?displayProperty=fullName>
