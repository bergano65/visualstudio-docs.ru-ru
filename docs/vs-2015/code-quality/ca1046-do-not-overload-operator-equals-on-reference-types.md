---
title: 'CA1046: Не перегружайте оператор равенства для ссылочных типов | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 05c58c3b136c52ace4e683c3d42d0d6417ff4a08
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183409"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: не перегружайте оператор равенства для ссылочных типов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытом или вложенном открытый ссылочный тип перегружает оператор равенства.

## <a name="rule-description"></a>Описание правила
 Реализация оператора равенства по умолчанию почти всегда правильно работает для ссылочных типов. По умолчанию две ссылки равны, если они указывают на один объект.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите реализацию оператора равенства.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если ссылочный тип ведет себя как встроенного типа значения. Если он имеет значение для выполнения сложения или вычитания для экземпляров типа, верно, вероятно, реализует оператор равенства и подавить нарушение.

## <a name="example"></a>Пример
 Следующий пример демонстрирует поведение по умолчанию при сравнении двух ссылок.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>Пример
 Следующее приложение сравниваются несколько ссылок.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 В этом примере формируются следующие данные:

 **= новый (2,2) и b = равны новый (2,2)? Не**
**c и идентичны? Да**
**b и являются ==? Не**
**c и являются ==? Да**
## <a name="related-rules"></a>Связанные правила
 [CA1013: перегружайте оператор равенства при перегрузке сложения и вычитания](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>См. также
 <xref:System.Object.Equals%2A?displayProperty=fullName> [Операторы равенства](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



