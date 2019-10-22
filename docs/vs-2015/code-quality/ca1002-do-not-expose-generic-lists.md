---
title: 'CA1002: не предоставляйте универсальные списки | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2a1d8ea70ca86cbb2f38afff48fe37b414b70e88
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646314"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: не следует раскрывать универсальные списки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип содержит видимый извне член, который является типом <xref:System.Collections.Generic.List%601?displayProperty=fullName>, возвращает тип <xref:System.Collections.Generic.List%601?displayProperty=fullName>, а сигнатура содержит параметр <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> — это универсальная коллекция, предназначенная для повышения производительности и без наследования. <xref:System.Collections.Generic.List%601?displayProperty=fullName> не содержит виртуальные члены, упрощающие изменение поведения унаследованного класса. Следующие универсальные коллекции предназначены для наследования и должны предоставляться вместо <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените тип <xref:System.Collections.Generic.List%601?displayProperty=fullName> на одну из универсальных коллекций, предназначенных для наследования.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если только сборка, вызывающая это предупреждение, не является повторно используемой библиотекой. Например, можно было бы отключить это предупреждение в приложении, настроенном для производительности, в котором было получено выигрыш в производительности от использования универсальных списков.

## <a name="related-rules"></a>Связанные правила
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: используйте универсальные объекты, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также раздел
 [Универсальные шаблоны](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
