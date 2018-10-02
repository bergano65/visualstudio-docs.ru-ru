---
title: 'CA1002: Не следует раскрывать универсальные списки | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 03435b59381f5127aeb7662df16c11e1e085824d
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592161"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: не следует раскрывать универсальные списки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1002: не следует раскрывать универсальные списки](https://docs.microsoft.com/visualstudio/code-quality/ca1002-do-not-expose-generic-lists).

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип содержит видимое извне элемент, который <xref:System.Collections.Generic.List%601?displayProperty=fullName> введите возвращает <xref:System.Collections.Generic.List%601?displayProperty=fullName> типа, либо, сигнатура которого содержит <xref:System.Collections.Generic.List%601?displayProperty=fullName> параметра.

## <a name="rule-description"></a>Описание правила
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> является универсальной коллекцией, предназначенный для повышения производительности и не для наследования. <xref:System.Collections.Generic.List%601?displayProperty=fullName> не содержит виртуальных членов, которые упрощают процесс изменить поведение унаследованного класса. Следующие универсальные коллекции предназначены для наследования и должны предоставляться вместо <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

-   <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

-   <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените <xref:System.Collections.Generic.List%601?displayProperty=fullName> типа к одному из универсальных коллекций, которые разработаны для наследования.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если сборку, которая выдает следующее предупреждение не должен быть многократно используемой библиотеки. Например можно с уверенностью отключить это предупреждение в приложении производительность где выигрыш от использования универсальные списки выигрыш в производительности.

## <a name="related-rules"></a>Связанные правила
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: используйте универсальные объекты, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также
 [Универсальные шаблоны](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)



