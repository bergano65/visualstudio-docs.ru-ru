---
title: 'CA2224: переопределение Equals при перегрузке оператора равенства | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 39272790b6ef366c64d45e0aea238606d0b62bf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538640"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224. Переопределяйте Equals при перегрузке оператора равенства
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый тип реализует оператор равенства, но не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Описание правила
 Оператор равенства должен быть синтаксически удобным способом доступа к функциональности <xref:System.Object.Equals%2A> метода. При реализации оператора равенства его логика должна быть идентична этой <xref:System.Object.Equals%2A> .

 Компилятор C# выдает предупреждение, если код нарушает это правило.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, необходимо либо удалить реализацию оператора равенства, либо переопределить, чтобы <xref:System.Object.Equals%2A> два метода возвращали одинаковые значения. Если оператор равенства не приводит к несогласованному поведению, можно устранить нарушение, предоставив реализацию <xref:System.Object.Equals%2A> , которая вызывает <xref:System.Object.Equals%2A> метод в базовом классе.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно спокойно отключить предупреждение из этого правила, если оператор равенства возвращает то же значение, что и унаследованная реализация <xref:System.Object.Equals%2A> . Раздел "пример" содержит тип, который может безопасно отключить предупреждение из этого правила.

## <a name="examples-of-inconsistent-equality-definitions"></a>Примеры непротиворечивых определений равенства

### <a name="description"></a>Описание
 В следующем примере показан тип с непротиворечивыми определениями равенства. `BadPoint` изменяет значение равенства, предоставляя пользовательскую реализацию оператора равенства, но не переопределяет <xref:System.Object.Equals%2A> его таким образом, что он ведет себя одинаково.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>Пример
 Следующий код проверяет поведение `BadPoint` .

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 В этом примере формируются следующие данные:

 **a = ([0] 1, 1) и b = ([1] 2, 2) равны? Нет** 
 **a = = b? ** 
 **Значения a1 и a не равны? Да** 
 **a1 = = a? Да** 
 **б и бкопи равны? Нет** 
 **b = = бкопи? Да**
## <a name="example"></a>Пример
 В следующем примере показан тип, который технически нарушает данное правило, но не работает в несогласованном режиме.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>Пример
 Следующий код проверяет поведение `GoodPoint` .

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 В этом примере формируются следующие данные:

 **a = (1, 1) и b = (2, 2) равны? Нет** 
 **a = = b? ** 
 **Значения a1 и a не равны? Да** 
 **a1 = = a? Да** 
 **б и бкопи равны? Да** 
 **b = = бкопи? Да**
## <a name="class-example"></a>Пример класса

### <a name="description"></a>Описание
 В следующем примере показан класс (ссылочный тип), нарушающий это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>Пример
 В следующем примере нарушение устраняется путем переопределения <xref:System.Object.Equals%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>Пример структуры

### <a name="description"></a>Описание
 В следующем примере показана структура (тип значения), которая нарушает данное правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>Пример
 В следующем примере нарушение устраняется путем переопределения <xref:System.ValueType.Equals%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1046. Не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225. Для перегрузок операторов существуют варианты с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226. Перегрузки операторов должны быть симметричными](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218. Переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231. Перегрузите оператор равенства на переопределяющем типе ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
