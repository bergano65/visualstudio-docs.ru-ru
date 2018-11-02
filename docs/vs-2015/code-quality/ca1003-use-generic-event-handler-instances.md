---
title: 'CA1003: Используйте экземпляры обработчика универсальных событий | Документация Майкрософт'
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
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f3c2cf2ad59f7ade337c84f13133bb5181afb615
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929092"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: используйте экземпляры обработчика универсальных событий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип содержит делегат, возвращающий значение void, сигнатура которого содержит два параметра (первый объект, а второй — тип, который может быть назначен EventArgs) и включенная сборка предназначена [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Описание правила
 Прежде чем [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], чтобы передать пользовательские данные в обработчик событий, новый делегат пришлось объявить, задает класс, который является производным от <xref:System.EventArgs?displayProperty=fullName> класса. Это больше не имеет значение true, если в [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], который появился <xref:System.EventHandler%601?displayProperty=fullName> делегировать. Этот универсальный делегат позволяет любой класс, производный от <xref:System.EventArgs> должна использоваться вместе с обработчик событий.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите делегат и замените его использование с помощью <xref:System.EventHandler%601?displayProperty=fullName> делегировать. Если делегат является автоматически создано [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] компилятора, измените синтаксис объявления событий следует использовать <xref:System.EventHandler%601?displayProperty=fullName> делегировать.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано делегат, который нарушает правило. В [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] примере комментариев описано, как изменить пример в соответствии с правилом. Например C# ниже приведен пример, показывающий измененный код.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Пример
 В следующем примере удаляется объявление делегата из предыдущего примера, соответствующий этому правилу, и заменяет его использование в `ClassThatRaisesEvent` и `ClassThatHandlesEvent` методы с помощью <xref:System.EventHandler%601?displayProperty=fullName> делегировать.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: используйте универсальные объекты, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также
 [Универсальные шаблоны](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)



