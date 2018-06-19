---
title: 'CA1002: не следует раскрывать универсальные списки'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a2131ef8cb0b8f0ba540d7403d7c5f8dbb8b89df
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31901100"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: не следует раскрывать универсальные списки
|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип содержит Внешне видимый член, <xref:System.Collections.Generic.List%601?displayProperty=fullName> введите возвращает <xref:System.Collections.Generic.List%601?displayProperty=fullName> типа или, подпись которого включает <xref:System.Collections.Generic.List%601?displayProperty=fullName> параметра.

## <a name="rule-description"></a>Описание правила
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> — Это универсальная коллекция, предназначенная для производительности и не для наследования. <xref:System.Collections.Generic.List%601?displayProperty=fullName> не содержит виртуальных членов, которые упрощают процесс изменить поведение унаследованного класса. Следующие универсальные коллекции предназначены для наследования и должен быть предоставлен вместо <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

-   <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

-   <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, измените <xref:System.Collections.Generic.List%601?displayProperty=fullName> типа в один из универсальных коллекций, которые предназначены для наследования.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если сборки, которая вызывает это предупреждение не рассчитан на всестороннее библиотеки многократного использования. Например можно с уверенностью отключить это предупреждение в приложении производительность где выигрыш от использования универсальные списки выигрыш в производительности.

## <a name="related-rules"></a>Связанные правила
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: используйте универсальные объекты, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)