---
title: 'CA2218: переопределяйте GetHashCode при переопределении Equals'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3bcf3d8c5f9780bcd245af7d5687797fce35ba9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: переопределяйте GetHashCode при переопределении Equals
|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый тип переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> , но не переопределяет <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 <xref:System.Object.GetHashCode%2A> Возвращает значение, на основе текущего экземпляра, используемое для алгоритмов хэширования и структур данных, например в хэш-таблице. Два объекта, которые имеют одинаковый тип и равны должен возвращать одинаковые хэш-код для обеспечения правильной работы экземпляров следующих типов:

-   <xref:System.Collections.Hashtable?displayProperty=fullName>

-   <xref:System.Collections.SortedList?displayProperty=fullName>

-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

-   <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

-   <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

-   <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

-   Типы, реализующие <xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, необходимо предоставить реализацию <xref:System.Object.GetHashCode%2A>. Для пары объектов того же типа, необходимо убедиться, что реализация возвращает то же значение, если реализация <xref:System.Object.Equals%2A> возвращает `true` для пары.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="class-example"></a>Пример класса

### <a name="description"></a>Описание
 В следующем примере класс (ссылочный тип), нарушающий это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]

### <a name="comments"></a>Комментарии
 В следующем примере нарушение устраняется путем переопределения <xref:System.Object.GetHashCode>.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]

## <a name="structure-example"></a>Пример структуры

### <a name="description"></a>Описание
 В следующем примере показана структура (тип значения), нарушающий это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]

### <a name="comments"></a>Комментарии
 В следующем примере нарушение устраняется путем переопределения <xref:System.Object.GetHashCode>.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1046: не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: для перезагрузок оператора существуют дополнения с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: перегрузки операторов должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>См. также
 <xref:System.Object.Equals%2A?displayProperty=fullName> <xref:System.Object.GetHashCode%2A?displayProperty=fullName> <xref:System.Collections.Hashtable?displayProperty=fullName> [Операторы равенства](/dotnet/standard/design-guidelines/equality-operators)