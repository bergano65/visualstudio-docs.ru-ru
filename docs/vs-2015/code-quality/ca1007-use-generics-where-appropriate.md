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
ms.openlocfilehash: 4ee33305c1ae0f15e5d8f390a4b65d62c87b6904
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547944"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007. По возможности используйте универсальные объекты
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод, видимый извне, содержит ссылочный параметр типа <xref:System.Object?displayProperty=fullName> и содержащий целевые объекты сборки [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="rule-description"></a>Описание правила
 Ссылочный параметр — это параметр, который изменяется с помощью `ref` `ByRef` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ключевого слова (in). Тип аргумента, передаваемый для ссылочного параметра, должен точно совпадать с типом ссылочного параметра. Чтобы использовать тип, производный от типа ссылочного параметра, необходимо сначала привести тип и присвоить переменной ссылочного типа параметра. Использование универсального метода позволяет передавать в метод все типы с ограничениями без предварительного приведения типа к типу ссылочного параметра.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте метод универсальным и замените <xref:System.Object> параметр с помощью параметра типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показана подпрограммы подкачки общего назначения, реализованная как неуниверсальные и универсальные методы. Обратите внимание, насколько эффективно перемещаются строки с помощью универсального метода по сравнению с неуниверсальным методом.

 [!code-csharp[FxCop.Design.UseGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/cs/FxCop.Design.UseGenerics.cs#1)]
 [!code-vb[FxCop.Design.UseGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/vb/FxCop.Design.UseGenerics.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1005. Не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010. Коллекции должны реализовать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000. Не объявляйте статические члены в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002. Не предоставляйте универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006. Не создавайте вложенные универсальные типы в сигнатурах членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004. Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003. Используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>См. также:
 [Универсальные шаблоны](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
