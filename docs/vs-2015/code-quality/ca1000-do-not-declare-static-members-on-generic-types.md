---
title: 'CA1000: не объявляйте статические члены в универсальных типах | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ef6c98c2808e639570b51d485df90bbdab72c43
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646366"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: не объявляйте статические элементы в универсальных типах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Видимый извне универсальный тип содержит элемент `static` (`Shared` в Visual Basic).

## <a name="rule-description"></a>Описание правила
 При вызове `static` универсального типа аргумент типа должен быть указан для типа. При вызове универсального экземпляра элемента, не поддерживающего вывод типа, для элемента нужно указать аргумент типа. Синтаксис для указания аргумента типа в этих двух случаях отличается и легко путают, как показано в следующих вызовах:

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

 Как правило, следует избегать использования обоих предыдущих объявлений, чтобы аргумент типа не обязательно был указан при вызове элемента. Это приводит к синтаксису вызова членов в универсальных шаблонах, которые не отличаются от синтаксиса для неуниверсальных типов. Дополнительные сведения см. в разделе [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите статический член или измените его на элемент экземпляра.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Предоставление универсальных шаблонов в синтаксисе, который легко понять и использовать, сокращает время, необходимое для изучения и увеличения скорости внедрения новых библиотек.

## <a name="related-rules"></a>Связанные правила
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1002: не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: используйте универсальные объекты, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также раздел
 [Универсальные шаблоны](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
