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
ms.openlocfilehash: 34318d3fb01f3f8dee50da2bc534908cecbdaf32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646300"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: используйте экземпляры обработчика универсальных событий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип содержит делегат, возвращающий значение void, сигнатура которого содержит два параметра (первый объект и второй тип, который может быть назначен EventArgs), и содержащая его сборка предназначена для [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Описание правила
 Прежде чем [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], чтобы передать пользовательские данные в обработчик событий, пришлось бы объявить новый делегат, который указал класс, производный от класса <xref:System.EventArgs?displayProperty=fullName>. Он больше не является верным в [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], в котором появился делегат <xref:System.EventHandler%601?displayProperty=fullName>. Этот универсальный делегат позволяет использовать любой класс, производный от <xref:System.EventArgs>, вместе с обработчиком событий.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите делегат и замените его использование с помощью делегата <xref:System.EventHandler%601?displayProperty=fullName>. Если делегат создается автоматически компилятором [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], измените синтаксис объявления события, чтобы использовать делегат <xref:System.EventHandler%601?displayProperty=fullName>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан делегат, нарушающий правило. В [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] примере комментарии описывают, как изменить пример для удовлетворения правила. В C# примере ниже показан измененный код.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Пример
 В следующем примере удаляется объявление делегата из предыдущего примера, которое удовлетворяет правилу, и заменяет его использование в методах `ClassThatRaisesEvent` и `ClassThatHandlesEvent` с помощью делегата <xref:System.EventHandler%601?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: используйте универсальные объекты, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также раздел
 [Универсальные шаблоны](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
