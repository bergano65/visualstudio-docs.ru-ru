---
title: 'CA1007: используйте универсальные шаблоны, где это уместно | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 22c9bac17a957438ee8d2a6f4b634f30604ed1ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668960"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: используйте универсальные методы, если это уместно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод, видимый извне, содержит ссылочный параметр типа <xref:System.Object?displayProperty=fullName>, а содержащий целевую сборку [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Описание правила
 Параметр ссылки — это параметр, который изменяется с помощью ключевого слова `ref` (`ByRef` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Тип аргумента, передаваемый для ссылочного параметра, должен точно совпадать с типом ссылочного параметра. Чтобы использовать тип, производный от типа ссылочного параметра, необходимо сначала привести тип и присвоить переменной ссылочного типа параметра. Использование универсального метода позволяет передавать в метод все типы с ограничениями без предварительного приведения типа к типу ссылочного параметра.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте метод универсальным и замените параметр <xref:System.Object> с помощью параметра типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показана подпрограммы подкачки общего назначения, реализованная как неуниверсальные и универсальные методы. Обратите внимание, насколько эффективно перемещаются строки с помощью универсального метода по сравнению с неуниверсальным методом.

 [!code-csharp[FxCop.Design.UseGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/cs/FxCop.Design.UseGenerics.cs#1)]
 [!code-vb[FxCop.Design.UseGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/vb/FxCop.Design.UseGenerics.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>См. также раздел
 [Универсальные шаблоны](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
