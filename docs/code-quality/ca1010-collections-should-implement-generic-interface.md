---
title: CA1010. Коллекции должны реализовать универсальный интерфейс
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a62120babe98ead6d78b568bc630f46a386edf02
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842648"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010. Коллекции должны реализовать универсальный интерфейс

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип реализует <xref:System.Collections.IEnumerable?displayProperty=fullName> интерфейса, но не реализует <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> интерфейс и содержащего .NET целевые объекты сборки. Это правило не учитывает типы, реализующие <xref:System.Collections.IDictionary?displayProperty=fullName>.

По умолчанию это правило считывает только типы, видимые извне, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Чтобы расширить возможности использования коллекции, реализуйте один из универсальных интерфейсов коллекции. Вы можете использовать коллекцию для заполнения типы универсальных коллекций, таких как следующие:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, реализуйте один из следующих универсальных интерфейсов:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила; Тем не менее использование коллекции будет более ограничены.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```ini
dotnet_code_quality.ca1010.api_surface = private, internal
```

В этой категории (структуры) можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Пример нарушения

В примере показан класс (ссылочный тип), является производным от неуниверсального `CollectionBase` класс, который нарушает это правило.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Чтобы устранить нарушение этого правила, выполните одно из следующих действий.

- Реализуйте универсальные интерфейсы.
- Измените базовый класс для типа, который уже реализует обеих универсальных и неуниверсальных интерфейсов, таких как `Collection<T>` класса.

## <a name="fix-by-base-class-change"></a>Исправить путем замены базового класса

В следующем примере нарушение устраняется путем изменения базового класса коллекции с неуниверсального `CollectionBase` класса к общим `Collection<T>` (`Collection(Of T)` в Visual Basic) класса.

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

Изменение базового класса уже выпущенного класса считается критическим изменением для существующих потребителей.

## <a name="fix-by-interface-implementation"></a>Исправление посредством реализации интерфейсов

В следующем примере устраняется нарушение путем реализации этих универсальных интерфейсов: `IEnumerable<T>`, `ICollection<T>`, и `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, и `IList(Of T)` в Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA1005: Избегайте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000: Не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: Не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Не вкладывайте универсальные типы в сигнатурах членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Используйте универсальные типы в том случае, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также

- [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)