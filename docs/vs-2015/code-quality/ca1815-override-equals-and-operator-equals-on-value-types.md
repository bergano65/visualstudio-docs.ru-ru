---
title: 'CA1815: переопределение Equals и оператора Equals для типов значений | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bb9574eb6e9f907d4b1fcc74f50fca0e7db85253
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668396"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: следует переопределять равенства и равенства операторов в типах значений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый тип значения не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> или не реализует оператор равенства (= =). Это правило не проверяет перечисления.

## <a name="rule-description"></a>Описание правила
 Для типов значений унаследованная реализация <xref:System.Object.Equals%2A> использует библиотеку отражения и сравнивает содержимое всех полей. Отражение является процессом, требующим с точки зрения вычислений больших затрат, и сравнение каждого поля на равенство может быть лишним. Если предполагается, что пользователи будут сравнивать или сортировать экземпляры или использовать их в качестве ключей хэш-таблицы, тип значения должен реализовывать <xref:System.Object.Equals%2A>. Если язык программирования поддерживает перегрузку операторов, также необходимо предоставить реализацию операторов равенства и неравенства.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, предоставьте реализацию <xref:System.Object.Equals%2A>. Если это возможно, реализуйте оператор равенства.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если экземпляры типа значения не будут сравниваться друг с другом.

## <a name="example-of-a-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 В следующем примере показана структура (тип значения), которая нарушает данное правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>Пример исправления

### <a name="description"></a>Описание
 В следующем примере исправляется предыдущее нарушение путем переопределения <xref:System.ValueType.Equals%2A?displayProperty=fullName> и реализации операторов равенства (= =,! =).

### <a name="code"></a>Код
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2224: переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: перегрузки операторов должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>См. также раздел
 <xref:System.Object.Equals%2A?displayProperty=fullName>
