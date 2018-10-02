---
title: 'CA2224: Переопределяйте равенство при перегрузке оператора равенства | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cd7acd4b99d3278d75aa3721137511857e04fe7c
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591327"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: переопределяйте равенство при перегрузке оператора равенства
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2224: Переопределяйте равенство при перегрузке оператора равенства](https://docs.microsoft.com/visualstudio/code-quality/ca2224-override-equals-on-overloading-operator-equals).

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый тип реализует оператор равенства, но не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Оператор равенства должен быть синтаксически удобный способ доступа к функциям <xref:System.Object.Equals%2A> метод. При реализации оператора равенства, логику необходимо быть идентична <xref:System.Object.Equals%2A>.

 Компилятор C# выдает предупреждение, если код нарушает это правило.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, следует либо удалите реализацию оператора равенства, либо переопределить <xref:System.Object.Equals%2A> и иметь два метода возвращает те же значения. Если оператор равенства не вводит непредсказуемому поведению, можно устранить нарушение, предоставляющего реализацию <xref:System.Object.Equals%2A> , который вызывает <xref:System.Object.Equals%2A> метод в базовом классе.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить предупреждение из этого правила, если оператор равенства возвращает то же значение, что унаследованной реализации <xref:System.Object.Equals%2A>. В разделе примера содержит тип, который может безопасно подавить предупреждение из этого правила.

## <a name="examples-of-inconsistent-equality-definitions"></a>Примеры определений несогласованные равенства

### <a name="description"></a>Описание
 В примере показан тип с несогласованные определения равенства. `BadPoint` изменяет значение равенства, предоставляя пользовательскую реализацию оператора равенства, но не переопределяет <xref:System.Object.Equals%2A> , чтобы он ведет себя идентично.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>Пример
 Следующий код проверяет поведение `BadPoint`.

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 В этом примере формируются следующие данные:

 **= ([0] 1,1) и b = ([1] 2,2) равны? Не**
**a == b? Не**
**a1 и могут быть равно? Да**
**a1 ==? Да**
**b и bcopy равны? Не**
**b == bcopy? Да**
## <a name="example"></a>Пример
 В примере показан тип, который технически нарушает это правило, но не работает должным образом несогласованности.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>Пример
 Следующий код проверяет поведение `GoodPoint`.

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 В этом примере формируются следующие данные:

 **= (1,1) и b = (2,2) равны? Не**
**a == b? Не**
**a1 и могут быть равно? Да**
**a1 ==? Да**
**b и bcopy равны? Да**
**b == bcopy? Да**
## <a name="class-example"></a>Пример класса

### <a name="description"></a>Описание
 В следующем примере класса (ссылочный тип), который нарушает это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>Пример
 В следующем примере устраняется нарушение путем переопределения <xref:System.Object.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>Пример структуры

### <a name="description"></a>Описание
 В следующем примере структура (тип значения), который нарушает это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>Пример
 В следующем примере устраняется нарушение путем переопределения <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1046: не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: для перезагрузок оператора существуют дополнения с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: перегрузки операторов должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)



