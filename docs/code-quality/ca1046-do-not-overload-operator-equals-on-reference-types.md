---
title: 'CA1046: не перегружайте оператор равенства для ссылочных типов'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6809534d14b58d60759133e972b5220fcfd58d61
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: не перегружайте оператор равенства для ссылочных типов
|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или вложенный открытый ссылочный тип перегружает оператор равенства.

## <a name="rule-description"></a>Описание правила
 Реализация оператора равенства по умолчанию почти всегда правильно работает для ссылочных типов. По умолчанию две ссылки равны, если они указывают на один объект.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, удалите реализацию оператора равенства.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно отключать предупреждение из этого правила, если ссылочный тип ведет себя как встроенный тип значения. Это может применяться для выполнения сложения или вычитания для экземпляров типа, правильность, возможно, для реализации оператора равенства и отключение нарушение.

## <a name="example"></a>Пример
 В следующем примере показано поведение по умолчанию при сравнении двух ссылок.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>Пример
 В следующем приложении сравниваются несколько ссылок.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

 В этом примере формируются следующие данные:

 **= новый (2,2) и b = равны новый (2,2)? Не**
**c и которых равны? Да**
**b и являются ==? Не**
**c и являются ==? Да**
## <a name="related-rules"></a>Связанные правила
 [CA1013: перегружайте оператор равенства при перегрузке сложения и вычитания](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>См. также
 <xref:System.Object.Equals%2A?displayProperty=fullName> [Операторы равенства](/dotnet/standard/design-guidelines/equality-operators)