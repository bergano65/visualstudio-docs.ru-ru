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
ms.openlocfilehash: 66bb2b2229608c1a7710b7c5c71cbc0d701234e3
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714387"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003. Используйте экземпляры обработчика универсальных событий

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Тип содержит делегат, возвращающий значение void и сигнатура которого содержит два параметра (первый объект, а второй — тип, который может быть назначен EventArgs) и содержащий .NET целевые объекты сборки.

По умолчанию это правило считывает только типы, видимые извне, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

До появления .NET, для передачи пользовательских сведений в обработчик событий, новый делегат приходилось объявляться, задает класс, который является производным от <xref:System.EventArgs?displayProperty=fullName> класса. В .NET, универсального <xref:System.EventHandler%601?displayProperty=fullName> делегат позволяет любой класс, производный от <xref:System.EventArgs> должна использоваться вместе с обработчик событий.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, удалите делегат и замените его использование с помощью <xref:System.EventHandler%601?displayProperty=fullName> делегировать.

Если делегат создается автоматически с помощью компилятора Visual Basic, измените синтаксис объявления событий следует использовать <xref:System.EventHandler%601?displayProperty=fullName> делегировать.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```ini
dotnet_code_quality.ca1003.api_surface = private, internal
```

В этой категории (структуры) можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере показано делегат, который нарушает правило. В примере Visual Basic комментарии описывается, как изменить пример в соответствии с правилом. Например C# ниже приведен пример, показывающий измененный код.

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

Следующий фрагмент кода удаляет объявление делегата из предыдущего примера, который удовлетворяет правилу. Он заменяет его использование в `ClassThatRaisesEvent` и `ClassThatHandlesEvent` методы с помощью <xref:System.EventHandler%601?displayProperty=fullName> делегировать.

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA1005: Избегайте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010: Коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000: Не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: Не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Не вкладывайте универсальные типы в сигнатурах членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007: Используйте универсальные типы в том случае, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также

- [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)