---
title: CA1003. Используйте экземпляры обработчика универсальных событий
ms.date: 03/11/2019
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
ms.openlocfilehash: c654da177e4a9cf820887cf74977a4c3da5a57b6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236648"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003. Используйте экземпляры обработчика универсальных событий

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Тип содержит делегат, возвращающий void, сигнатура которого содержит два параметра (первый объект и второй тип, который может быть назначен EventArgs), а содержащая сборка предназначена для .NET.

По умолчанию это правило рассматривает только видимые извне типы, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Перед тем как использовать .NET для передачи пользовательских данных в обработчик событий, пришлось бы объявить новый делегат, который указал класс, производный от <xref:System.EventArgs?displayProperty=fullName> класса. В .NET универсальный <xref:System.EventHandler%601?displayProperty=fullName> делегат позволяет использовать любой класс, производный от <xref:System.EventArgs> , вместе с обработчиком событий.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, удалите делегат и замените его использование с помощью <xref:System.EventHandler%601?displayProperty=fullName> делегата.

Если делегат создается автоматически компилятором Visual Basic, измените синтаксис объявления события, чтобы он <xref:System.EventHandler%601?displayProperty=fullName> использовал делегат.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca1003.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (конструктор). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере показан делегат, нарушающий правило. В Visual Basic примере комментарии описывают, как изменить пример для удовлетворения правила. В C# примере ниже показан измененный код.

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

Следующий фрагмент кода удаляет объявление делегата из предыдущего примера, удовлетворяющего правилу. Он заменяет его использование в `ClassThatRaisesEvent` методах и `ClassThatHandlesEvent` с помощью <xref:System.EventHandler%601?displayProperty=fullName> делегата.

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA1005: Избегайте чрезмерных параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010 Коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000: Не объявляйте статические члены в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002 Не предоставляйте универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006 Не вкладывать универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004 Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007: Используйте универсальные шаблоны там, где это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также

- [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)