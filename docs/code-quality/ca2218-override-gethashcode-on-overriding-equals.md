---
title: CA2218. Переопределяйте GetHashCode при переопределении Equals
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 750a574eec5beedadce387109a5bd941d4e0e413
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971588"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218. Переопределяйте GetHashCode при переопределении Equals

|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый тип переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> , но не переопределяет <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 <xref:System.Object.GetHashCode%2A> Возвращает значение, в зависимости от текущего экземпляра, который подходит для алгоритмов хэширования и структур данных, например хэш-таблице. Два объекта, которые имеют одинаковый тип и равны должен возвращать одинаковый хэш-код для обеспечения правильной работы экземпляров следующих типов:

- <xref:System.Collections.Hashtable?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

- Типы, реализующие <xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, предоставлять реализацию метода <xref:System.Object.GetHashCode%2A>. Для пары объектов одного типа, необходимо убедиться, что реализация возвращает то же значение, если ваша реализация <xref:System.Object.Equals%2A> возвращает `true` для пары.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="class-example"></a>Пример класса

### <a name="description"></a>Описание:
 В следующем примере класса (ссылочный тип), который нарушает это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]

### <a name="comments"></a>Комментарии
 В следующем примере устраняется нарушение путем переопределения <xref:System.Object.GetHashCode>.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]

## <a name="structure-example"></a>Пример структуры

### <a name="description"></a>Описание
 В следующем примере структура (тип значения), который нарушает это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]

### <a name="comments"></a>Комментарии
 В следующем примере устраняется нарушение путем переопределения <xref:System.Object.GetHashCode>.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1046: Не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Оператор дополнения с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Операторы должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: перегрузите оператор равенства на переопределяющем типе ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>См. также

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [Операторы равенства](/dotnet/standard/design-guidelines/equality-operators)