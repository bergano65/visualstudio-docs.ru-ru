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
ms.openlocfilehash: 70a418b211cd4340dba9c15f0bf52e3cdfdf8e8f
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547902"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010. Коллекции должны реализовать универсальный интерфейс

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип реализует <xref:System.Collections.IEnumerable?displayProperty=fullName> интерфейс, но не <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> реализует интерфейс, а включающая сборка предназначена для .NET. Это правило игнорирует типы, реализующие <xref:System.Collections.IDictionary?displayProperty=fullName>.

По умолчанию это правило рассматривает только видимые извне типы, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Чтобы расширить возможности использования коллекции, реализуйте один из универсальных интерфейсов коллекции. Затем можно использовать коллекцию для заполнения типов универсальных коллекций, таких как следующие:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, реализуйте один из следующих интерфейсов универсальной коллекции:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Можно спокойно отключить предупреждение из этого правила. Однако использование коллекции будет ограничено.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca1010.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (конструктор). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Пример нарушения

В следующем примере показан класс (ссылочный тип), который является производным от неуниверсального `CollectionBase` класса, который нарушает это правило.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Чтобы устранить нарушение этого правила, выполните одно из следующих действий.

- Реализуйте универсальные интерфейсы.
- Измените базовый класс на тип, который уже реализует универсальные и неуниверсальные интерфейсы, такие как `Collection<T>` класс.

## <a name="fix-by-base-class-change"></a>Исправление по изменению базового класса

Следующий пример устраняет нарушение, изменяя базовый класс коллекции с неуниверсального `CollectionBase` класса на универсальный `Collection<T>` (`Collection(Of T)` в Visual Basic) класс.

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

Изменение базового класса уже выпущенного класса считается критическим изменением существующих потребителей.

## <a name="fix-by-interface-implementation"></a>Исправление по реализации интерфейса

В следующем примере нарушение устраняется путем реализации этих универсальных интерфейсов `ICollection<T>`: `IEnumerable<T>`, `IList<T>` и`IEnumerable(Of T)`( `ICollection(Of T)`, и `IList(Of T)` в Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA1005: Избегайте чрезмерных параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000: Не объявляйте статические члены в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002 Не предоставляйте универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006 Не вкладывать универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004 Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Использование экземпляров универсальных обработчиков событий](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Используйте универсальные шаблоны там, где это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также

- [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)