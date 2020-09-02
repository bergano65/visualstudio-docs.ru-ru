---
title: 'CA1010: коллекции должны реализовывать универсальный интерфейс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b141d755c717ad6650d2a49c98c2b26547066b7a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545526"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010. Коллекции должны реализовать универсальный интерфейс
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, видимый извне, реализует <xref:System.Collections.IEnumerable?displayProperty=fullName> интерфейс, но не реализует <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> интерфейс и содержащий целевые объекты сборки [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] . Это правило игнорирует типы, реализующие <xref:System.Collections.IDictionary?displayProperty=fullName> .

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

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно спокойно отключить предупреждение из этого правила. Однако коллекция будет иметь более ограниченное использование.

## <a name="example-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 В следующем примере показан класс (ссылочный тип), который является производным от неуниверсального `CollectionBase` класса, который нарушает это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericViolation/cs/FxCop.Design.CollectionsGenericViolation.cs#1)]

### <a name="comments"></a>Комментарии
 Чтобы устранить нарушение этого нарушения, следует либо реализовать универсальные интерфейсы, либо изменить базовый класс на тип, который уже реализует универсальные и неуниверсальные интерфейсы, такие как `Collection<T>` класс.

## <a name="fix-by-base-class-change"></a>Исправление по изменению базового класса

### <a name="description"></a>Описание
 Следующий пример устраняет нарушение, изменяя базовый класс коллекции с неуниверсального `CollectionBase` класса на универсальный `Collection<T>` ( `Collection(Of T)` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) класс.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericBase/cs/FxCop.Design.CollectionsGenericBase.cs#1)]

### <a name="comments"></a>Комментарии
 Изменение базового класса уже выпущенного класса считается критическим изменением существующих потребителей.

## <a name="fix-by-interface-implementation"></a>Исправление по реализации интерфейса

### <a name="description"></a>Описание
 В следующем примере нарушение устраняется путем реализации этих универсальных интерфейсов: `IEnumerable<T>` , `ICollection<T>` и `IList<T>` ( `IEnumerable(Of T)` , `ICollection(Of T)` и `IList(Of T)` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericInterface/cs/FxCop.Design.CollectionsGenericInterface.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1005. Не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000. Не объявляйте статические члены в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002. Не предоставляйте универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006. Не создавайте вложенные универсальные типы в сигнатурах членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004. Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003. Используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007. По возможности используйте универсальные объекты](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также:
 [Универсальные шаблоны](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
