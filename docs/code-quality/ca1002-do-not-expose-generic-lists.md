---
title: CA1002. Не предоставляйте универсальные списки
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 621bb7292ca467d6d3197636f662a4662712d483
ms.sourcegitcommit: 0f44ec8ba0263056ad04d2d0dc904ad4206ce8fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766021"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002. Не предоставляйте универсальные списки

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Тип содержит видимый извне член, который является <xref:System.Collections.Generic.List%601?displayProperty=fullName> типом, <xref:System.Collections.Generic.List%601> Возвращает тип или сигнатура, в <xref:System.Collections.Generic.List%601> которой содержится параметр.

## <a name="rule-description"></a>Описание правила

<xref:System.Collections.Generic.List%601?displayProperty=fullName>— Это универсальная коллекция, предназначенная для повышения производительности, а не для наследования. <xref:System.Collections.Generic.List%601>не содержит виртуальные члены, упрощающие изменение поведения унаследованного класса. Следующие универсальные коллекции предназначены для наследования и должны быть предоставлены вместо <xref:System.Collections.Generic.List%601>.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, измените <xref:System.Collections.Generic.List%601?displayProperty=fullName> тип на одну из универсальных коллекций, предназначенных для наследования.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Не отключайте предупреждение из этого правила, если только сборка, вызывающая это предупреждение, не является повторно используемой библиотекой. Например, можно было бы отключить это предупреждение в приложении, настроенном для производительности, в котором было получено выигрыш в производительности от использования универсальных списков.

## <a name="related-rules"></a>Связанные правила

[CA1005: Избегайте чрезмерных параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010 Коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Не объявляйте статические члены в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1006 Не вкладывать универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004 Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Использование экземпляров универсальных обработчиков событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Используйте универсальные шаблоны там, где это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также

[Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)
