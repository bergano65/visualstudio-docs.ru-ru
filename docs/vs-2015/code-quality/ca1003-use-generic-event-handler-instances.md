---
title: 'CA1003: использование экземпляров обработчика универсальных событий | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ee0571e85a1d4ec9960e0235814fcb9d7adbd483
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539910"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003. Используйте экземпляры обработчика универсальных событий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип содержит делегат, возвращающий значение void, сигнатура которого содержит два параметра (первый объект и второй тип, который может быть назначен EventArgs), и содержащий целевые объекты сборки [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="rule-description"></a>Описание правила
 Прежде [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , чтобы передать пользовательские данные в обработчик событий, пришлось бы объявить новый делегат, который указал класс, производный от <xref:System.EventArgs?displayProperty=fullName> класса. Это больше не имеет значения в [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , в котором был введен <xref:System.EventHandler%601?displayProperty=fullName> делегат. Этот универсальный делегат позволяет использовать любой класс, производный от, <xref:System.EventArgs> вместе с обработчиком событий.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите делегат и замените его использование с помощью <xref:System.EventHandler%601?displayProperty=fullName> делегата. Если делегат создается автоматически [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] компилятором, измените синтаксис объявления события, чтобы он использовал <xref:System.EventHandler%601?displayProperty=fullName> делегат.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан делегат, нарушающий правило. В этом [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] примере комментарии описывают, как изменить пример для удовлетворения правила. Для примера на C# приведен пример, в котором показан измененный код.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Пример
 В следующем примере удаляется объявление делегата из предыдущего примера, которое удовлетворяет правилу, и заменяет его использование в `ClassThatRaisesEvent` `ClassThatHandlesEvent` методах и с помощью <xref:System.EventHandler%601?displayProperty=fullName> делегата.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1005. Не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010. Коллекции должны реализовать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000. Не объявляйте статические члены в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002. Не предоставляйте универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006. Не создавайте вложенные универсальные типы в сигнатурах членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004. Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007. По возможности используйте универсальные объекты](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также:
 [Универсальные шаблоны](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
