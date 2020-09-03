---
title: 'CA2227: свойства коллекции должны быть доступны только для чтения | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 17c4e2336a5c8bd8905d857dc8189a11f9fb6181
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540534"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227. Свойства, возвращающие коллекции, должны быть доступными только для чтения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Категория|Microsoft. Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Внешне видимое свойство, доступное для записи, является типом, реализующим <xref:System.Collections.ICollection?displayProperty=fullName> . Эти массивы, индексаторы (свойства с именем Item) и наборы разрешений игнорируются правилом.

## <a name="rule-description"></a>Описание правила
 Свойство коллекции, доступное для записи, позволяет пользователю заменить коллекцию совершенно другой коллекцией. Свойство только для чтения предотвращает замену коллекции, но по-прежнему допускает установку, настройку отдельных членов. Если замена коллекции является целью, предпочтительным шаблоном разработки является включение метода для удаления всех элементов из коллекции и метода для повторного заполнения коллекции. <xref:System.Collections.ArrayList.Clear%2A> <xref:System.Collections.ArrayList.AddRange%2A> Пример этого шаблона см. в методах и <xref:System.Collections.ArrayList?displayProperty=fullName> класса.

 Как двоичная, так и XML-сериализация поддерживают свойства только для чтения, являющиеся коллекциями. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>Класс имеет особые требования для типов, которые реализуют <xref:System.Collections.ICollection> и <xref:System.Collections.IEnumerable?displayProperty=fullName> для сериализации.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте свойство доступным только для чтения и, если оно требуется, добавьте методы для очистки и повторного заполнения коллекции.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан тип с доступным для записи свойством коллекции и показано, как можно заменить коллекцию напрямую. Кроме того, показан предпочтительный способ замены свойства коллекции, доступного только для чтения, с помощью `Clear` `AddRange` методов и.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1819. Свойства не должны возвращать массивы](../code-quality/ca1819-properties-should-not-return-arrays.md)
