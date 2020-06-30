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
ms.openlocfilehash: 6fcc4ae2a07eb7b1f155d6c65020e2c1a9ddc9f2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546852"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002. Не предоставляйте универсальные списки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип содержит видимый извне член, который является <xref:System.Collections.Generic.List%601?displayProperty=fullName> типом, возвращает <xref:System.Collections.Generic.List%601?displayProperty=fullName> тип или сигнатура, в которой содержится <xref:System.Collections.Generic.List%601?displayProperty=fullName> параметр.

## <a name="rule-description"></a>Описание правила
 <xref:System.Collections.Generic.List%601?displayProperty=fullName>— Это универсальная коллекция, предназначенная для повышения производительности и без наследования. <xref:System.Collections.Generic.List%601?displayProperty=fullName>не содержит виртуальные члены, упрощающие изменение поведения унаследованного класса. Следующие универсальные коллекции предназначены для наследования и должны быть предоставлены вместо <xref:System.Collections.Generic.List%601?displayProperty=fullName> .

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените <xref:System.Collections.Generic.List%601?displayProperty=fullName> тип на одну из универсальных коллекций, предназначенных для наследования.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если только сборка, вызывающая это предупреждение, не является повторно используемой библиотекой. Например, можно было бы отключить это предупреждение в приложении, настроенном для производительности, в котором было получено выигрыш в производительности от использования универсальных списков.

## <a name="related-rules"></a>Связанные правила
 [CA1005. Не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010. Коллекции должны реализовать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000. Не объявляйте статические члены в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006. Не создавайте вложенные универсальные типы в сигнатурах членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004. Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003. Используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007. По возможности используйте универсальные объекты](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также
 [Универсальные шаблоны](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
