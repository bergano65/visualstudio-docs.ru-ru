---
title: 'CA1036: Переопределяйте методы в сравнимых типах | Документация Майкрософт'
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
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 67fa52a674b9e3d77d7e3eed7493bf28c1b2514d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948791"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: переопределяйте методы в сравнимых типах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип реализует <xref:System.IComparable?displayProperty=fullName> интерфейс и не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> или не перегружает языковой оператор равенства, неравенства, меньше или больше. Правило сообщает о нарушениях, если тип наследует только реализацию интерфейса.

## <a name="rule-description"></a>Описание правила
 Типы, определяющие пользовательский порядок сортировки реализуют <xref:System.IComparable> интерфейс. <xref:System.IComparable.CompareTo%2A> Метод возвращает целочисленное значение, указывающее правильный порядок сортировки для двух экземпляров типа. Это правило определяет типы, установленные порядка сортировки. Это означает, что порядковое значение равенства, неравенства, меньше и больше не применяются. Если предоставить реализацию <xref:System.IComparable>, обычно необходимо также переопределить <xref:System.Object.Equals%2A> , возвращающий значения, которые соответствуют <xref:System.IComparable.CompareTo%2A>. При переопределении <xref:System.Object.Equals%2A> и при написании кода на языке, который поддерживает перегрузки операторов, также необходимо предоставить операторы, которые соответствуют <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, переопределите <xref:System.Object.Equals%2A>. Если язык программирования поддерживает перегрузку операторов, предоставьте следующие операторы:

- функции op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  В C#, токены, которые используются для представления этих операторов используются следующие: ==,! =, \<, и >.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, когда причиной нарушения является отсутствие операторов и язык программирования поддерживает перегрузку операторов, как в случае с Visual Basic .NET. Это также можно отключить предупреждение из этого правила, при его срабатывании на операторы равенства, отличные от функции op_Equality, если выяснится, что реализация операторов не имеет смысла в контексте приложения. Тем не менее, следует всегда через функции op_Equality и оператора ==, если переопределяет Object.Equals.

## <a name="example"></a>Пример
 Следующий пример содержит тип, который правильно реализует <xref:System.IComparable>. Комментарии к коду определить методы, которые удовлетворяют различные правила, которые связаны с <xref:System.Object.Equals%2A> и <xref:System.IComparable> интерфейс.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Пример
 Следующее приложение проверяет поведение <xref:System.IComparable> реализацию, которая была показана ранее.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>См. также
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [Операторы равенства](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



