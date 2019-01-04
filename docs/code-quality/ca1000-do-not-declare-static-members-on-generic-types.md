---
title: CA1000. Не объявляйте статические члены в универсальных типах
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f4f0a21f685cc4ff1edc54aa8002d6ecb3c28b9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890525"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000. Не объявляйте статические члены в универсальных типах

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Видимый извне тип универсального содержит `static` (`Shared` в Visual Basic) члена.

## <a name="rule-description"></a>Описание правила
 Когда `static` вызывается член универсального типа, аргумент типа должен быть указан для типа. При вызове универсального экземпляра элемента, не поддерживающего вывод типа, для элемента нужно указать аргумент типа. Синтаксис для определения аргумента типа в этих двух случаях разные и легко перепутать, как показывают следующие вызовы:

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

 Как правило оба предыдущих объявлений следует избегать, чтобы аргумент типа не должно быть задано при вызове члена. В результате синтаксис для вызова участников в универсальных шаблонах, которые ничем не отличается от синтаксиса для неуниверсальных. Дополнительные сведения см. в разделе [CA1004: Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите статический элемент или измените его на член экземпляра.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Использование универсальных типов в синтаксисе, который прост для понимания и использования сокращает время, необходимое для обучения и увеличивает скорость внедрения новых библиотек.

## <a name="related-rules"></a>Связанные правила
 [CA1005: Избегайте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1002: Не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Не вкладывайте универсальные типы в сигнатурах членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Используйте универсальные типы в том случае, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)