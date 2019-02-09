---
title: CA1007. По возможности используйте универсальные объекты
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f1cf2939f0484c6defb76b88fb072fcd4b51849b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922535"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007. По возможности используйте универсальные объекты

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Видимый извне метод содержит ссылочный параметр типа <xref:System.Object?displayProperty=fullName>и включенная сборка предназначена [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Описание правила
 Параметр ссылки — это параметр, измененный с использованием `ref` (`ByRef` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ключевое слово. Тип аргумента, переданное для ссылочного параметра должно совпадать с типом ссылочного параметра. Чтобы использовать тип, который является производным от типа ссылочного параметра, тип необходимо сначала привести и присваивается переменной ссылочного типа параметра. Использование универсального метода позволяет всех типов, ограничения, передаваемый в метод без предварительного приведения к типу параметра в ссылочный тип.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте метод универсальным и замените <xref:System.Object> параметра с помощью параметра типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано процедура замены общего назначения, реализованы в виде универсальных и неуниверсальных методов. Обратите внимание на то, насколько эффективно меняются местами строки с помощью метода по сравнению с неуниверсального метода.

 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1005: Избегайте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Не вкладывайте универсальные типы в сигнатурах членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>См. также
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)