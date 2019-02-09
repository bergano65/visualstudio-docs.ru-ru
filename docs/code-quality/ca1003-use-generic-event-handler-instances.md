---
title: CA1003. Используйте экземпляры обработчика универсальных событий
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 89ee70694d81253c66fc83062c9736ba63f7e6e6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907312"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003. Используйте экземпляры обработчика универсальных событий

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип содержит делегат, возвращающий значение void, сигнатура которого содержит два параметра (первый объект, а второй — тип, который может быть назначен EventArgs) и включенная сборка предназначена [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Описание правила
 Прежде чем [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], чтобы передать пользовательские данные в обработчик событий, новый делегат пришлось объявить, задает класс, который является производным от <xref:System.EventArgs?displayProperty=fullName> класса. Это больше не имеет значение true, если в [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], который появился <xref:System.EventHandler%601?displayProperty=fullName> делегировать. Этот универсальный делегат позволяет любой класс, производный от <xref:System.EventArgs> должна использоваться вместе с обработчик событий.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите делегат и замените его использование с помощью <xref:System.EventHandler%601?displayProperty=fullName> делегировать. Если делегат является автоматически создано [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] компилятора, измените синтаксис объявления событий следует использовать <xref:System.EventHandler%601?displayProperty=fullName> делегировать.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано делегат, который нарушает правило. В [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] примере комментариев описано, как изменить пример в соответствии с правилом. Например C# ниже приведен пример, показывающий измененный код.

 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

## <a name="example"></a>Пример
 В следующем примере удаляется объявление делегата из предыдущего примера, соответствующий этому правилу, и заменяет его использование в `ClassThatRaisesEvent` и `ClassThatHandlesEvent` методы с помощью <xref:System.EventHandler%601?displayProperty=fullName> делегировать.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1005: Избегайте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Не вкладывайте универсальные типы в сигнатурах членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Используйте универсальные типы в том случае, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также

- [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)