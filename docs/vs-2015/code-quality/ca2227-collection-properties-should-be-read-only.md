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
ms.openlocfilehash: 8aee6f7172414de809d964652411c1f077fe0cdd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658859"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: свойства коллекции должны иметь параметр "только для чтения"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Категория|Microsoft. Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Внешне видимое свойство, доступное для записи, является типом, реализующим <xref:System.Collections.ICollection?displayProperty=fullName>. Эти массивы, индексаторы (свойства с именем Item) и наборы разрешений игнорируются правилом.

## <a name="rule-description"></a>Описание правила
 Свойство коллекции, доступное для записи, позволяет пользователю заменить коллекцию совершенно другой коллекцией. Свойство только для чтения предотвращает замену коллекции, но по-прежнему допускает установку, настройку отдельных членов. Если замена коллекции является целью, предпочтительным шаблоном разработки является включение метода для удаления всех элементов из коллекции и метода для повторного заполнения коллекции. Пример использования этого шаблона см. в разделе методы <xref:System.Collections.ArrayList.Clear%2A> и <xref:System.Collections.ArrayList.AddRange%2A> класса <xref:System.Collections.ArrayList?displayProperty=fullName>.

 Как двоичная, так и XML-сериализация поддерживают свойства только для чтения, являющиеся коллекциями. Класс <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> имеет особые требования для типов, реализующих <xref:System.Collections.ICollection> и <xref:System.Collections.IEnumerable?displayProperty=fullName> для сериализации.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте свойство доступным только для чтения и, если оно требуется, добавьте методы для очистки и повторного заполнения коллекции.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан тип с доступным для записи свойством коллекции и показано, как можно заменить коллекцию напрямую. Кроме того, отображается предпочтительный способ замены свойства коллекции только для чтения с помощью методов `Clear` и `AddRange`.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1819: свойства не должны возвращать массивы](../code-quality/ca1819-properties-should-not-return-arrays.md)
