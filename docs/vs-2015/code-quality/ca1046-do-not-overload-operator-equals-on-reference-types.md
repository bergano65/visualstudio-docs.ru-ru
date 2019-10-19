---
title: 'CA1046: не перегружать оператор Equals для ссылочных типов | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 519faf2d49cb74d60d342d6bcf449f211076b0b4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661086"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: не перегружайте оператор равенства для ссылочных типов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или вложенный открытый ссылочный тип перегружает оператор равенства.

## <a name="rule-description"></a>Описание правила
 Реализация оператора равенства по умолчанию почти всегда правильно работает для ссылочных типов. По умолчанию две ссылки равны, если они указывают на один объект.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите реализацию оператора равенства.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждений из этого правила, если ссылочный тип ведет себя как встроенный тип значения. Если имеет смысл выполнять сложение или вычитание экземпляров типа, вероятно, необходимо реализовать оператор равенства и устранить нарушение.

## <a name="example"></a>Пример
 В следующем примере демонстрируется поведение по умолчанию при сравнении двух ссылок.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>Пример
 В следующем приложении сравниваются некоторые ссылки.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 В этом примере формируются следующие данные:

 **a = New (2, 2) и b = New (2, 2) равны? **@No__t_1**c и a не равны? Да** 
**б и a = =? Нет** 
**c и a = =? Да**
## <a name="related-rules"></a>Связанные правила
 [CA1013: перегружайте оператор равенства при перегрузке сложения и вычитания](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>См. также раздел
 <xref:System.Object.Equals%2A?displayProperty=fullName> [Операторы равенства](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
