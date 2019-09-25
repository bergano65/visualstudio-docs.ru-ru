---
title: CA2227. Свойства, возвращающие коллекции, должны быть доступными только для чтения
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 3d097a67c9a62a6847ff6ab0bb882257c082ca6f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231304"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227. Свойства, возвращающие коллекции, должны быть доступными только для чтения

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Категория|Microsoft. Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Внешне видимое свойство с возможностью записи имеет тип, реализующий <xref:System.Collections.ICollection?displayProperty=fullName>. Это правило игнорирует массивы, индексаторы (свойства с именем "Item") и наборы разрешений.

## <a name="rule-description"></a>Описание правила

Свойство коллекции, доступное для записи, позволяет пользователю заменить коллекцию совершенно другой коллекцией. Свойство только для чтения останавливает замену коллекции, но по-прежнему позволяет устанавливать отдельные элементы. Если замена коллекции является целью, предпочтительным шаблоном разработки является включение метода для удаления всех элементов из коллекции и метода для повторного заполнения коллекции. Пример этого <xref:System.Collections.ArrayList.Clear%2A> шаблона <xref:System.Collections.ArrayList.AddRange%2A> см. в <xref:System.Collections.ArrayList?displayProperty=fullName> методах и класса.

Как двоичная, так и XML-сериализация поддерживают свойства только для чтения, являющиеся коллекциями. Класс имеет особые требования для типов, которые реализуют <xref:System.Collections.IEnumerable?displayProperty=fullName> <xref:System.Collections.ICollection> и для сериализации. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, сделайте свойство доступным только для чтения. Если это требуется для разработки, добавьте методы для очистки и повторного заполнения коллекции.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Предупреждение можно отключить, если свойство является частью класса [Передача данных Object (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) .

В противном случае не отключайте предупреждения из этого правила.

## <a name="example"></a>Пример

В следующем примере показан тип с доступным для записи свойством коллекции и показано, как можно заменить коллекцию напрямую. Кроме того, он показывает предпочтительный способ замены свойства коллекции, доступного только для `Clear` чтения `AddRange` , с помощью методов и.

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Связанные правила

- [CA1819: Свойства не должны возвращать массивы](../code-quality/ca1819-properties-should-not-return-arrays.md)