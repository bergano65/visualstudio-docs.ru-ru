---
title: 'CA1003: используйте экземпляры обработчика универсальных событий'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e605cb0188ca72cb74905e34ee5196a07f748cd6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: используйте экземпляры обработчика универсальных событий
|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип содержит делегат, возвращающий значение void, сигнатура которого содержит два параметра (первый — объект, а второй тип, который может быть назначен EventArgs) и включенная сборка предназначена [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Описание правила
 Прежде чем [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], для передачи пользовательских сведений в обработчик событий, новый делегат требовалось объявлять, указанный класс, который является производным от <xref:System.EventArgs?displayProperty=fullName> класса. Это характерно для [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], который появился <xref:System.EventHandler%601?displayProperty=fullName> делегата. Этот универсальный делегат позволяет любой класс, производный от <xref:System.EventArgs> должна использоваться вместе с обработчик события.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, удалите делегат и замените его использование с помощью <xref:System.EventHandler%601?displayProperty=fullName> делегата. Если делегат является автоматически [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] компилятора, измените синтаксис в объявлении события для использования <xref:System.EventHandler%601?displayProperty=fullName> делегата.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано делегат, который нарушает правило. В [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] примере комментариях описано, как изменить пример в соответствии с правилом. Например, C# ниже приведен пример, показывающий измененный код.

 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

## <a name="example"></a>Пример
 В следующем примере удаляется объявление делегата из предыдущего примера, соответствующий этому правилу, которое заменяет его использование в `ClassThatRaisesEvent` и `ClassThatHandlesEvent` методов с помощью <xref:System.EventHandler%601?displayProperty=fullName> делегата.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: используйте универсальные объекты, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)