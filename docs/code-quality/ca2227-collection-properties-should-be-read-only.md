---
title: 'CA2227: свойства коллекции должны иметь параметр "только для чтения"'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 486a210b348149823e442ce12befb63e49b08390
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: свойства коллекции должны иметь параметр "только для чтения"
|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Категория|Microsoft.Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Видимый извне перезаписываемым свойством является тип, реализующий <xref:System.Collections.ICollection?displayProperty=fullName>. Массивы, индексы (свойства с именем «Item») и наборы разрешений учитываются этим правилом.

## <a name="rule-description"></a>Описание правила
 Свойство коллекции, допускающее запись позволяет пользователю заменять одну коллекцию полностью другой коллекцией. Свойство только для чтения предотвращает замену коллекции, но по-прежнему допускает установку, настройку отдельных членов. Если замена коллекции является целью, чтобы включить метод, чтобы удалить все элементы из коллекции и для повторного заполнения коллекции является предпочтительным вариантом разработки. В разделе <xref:System.Collections.ArrayList.Clear%2A> и <xref:System.Collections.ArrayList.AddRange%2A> методы <xref:System.Collections.ArrayList?displayProperty=fullName> класса, например, этот шаблон.

 Двоичный файл и XML-сериализация поддерживает свойства только для чтения, которые относятся к коллекциям. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> Класс имеет особые требования для типов, реализующих <xref:System.Collections.ICollection> и <xref:System.Collections.IEnumerable?displayProperty=fullName> чтобы сериализоваться.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, сделать свойство доступным только для чтения и, если это требуется для разработки, добавьте методы для очистки и повторного заполнения коллекции.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан тип со свойством коллекции, допускающее запись и показано, как коллекции может быть заменен напрямую. Кроме того, предпочтительный способ замены свойства только для чтения коллекцию с помощью `Clear` и `AddRange` показаны методы.

 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Связанные правила
 [CA1819: свойства не должны возвращать массивы](../code-quality/ca1819-properties-should-not-return-arrays.md)