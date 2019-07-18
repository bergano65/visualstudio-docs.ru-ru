---
title: CA1046. Не перегружайте оператор равенства для ссылочных типов | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c2d9e301b842e0cbd84e23b58310c6afad276b4a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696770"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046. Не перегружайте оператор равенства для ссылочных типов
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
 [CA1013: Перегружайте оператор равенства при перегрузке Добавление и вычитание](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>См. также
 <xref:System.Object.Equals%2A?displayProperty=fullName> [Операторы равенства](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
