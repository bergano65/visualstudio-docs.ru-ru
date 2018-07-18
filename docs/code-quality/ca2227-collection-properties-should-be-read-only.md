---
title: 'CA2227: свойства коллекции должны иметь параметр "только для чтения"'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: aa1d8644049f78eccfda7402360bdbc930b61601
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447678"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: свойства коллекции должны иметь параметр "только для чтения"

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Категория|Microsoft.Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Видимый извне, доступный для записи свойство имеет тип, реализующий <xref:System.Collections.ICollection?displayProperty=fullName>. Это правило не учитывает массивов, индексаторов (свойства с именем «Item») и наборы разрешений.

## <a name="rule-description"></a>Описание правила

Свойство коллекции, допускающее запись позволяет пользователю заменять одну коллекцию полностью другой коллекцией. Свойство только для чтения останавливает замену коллекции, но по-прежнему допускает настройку отдельных членов. Если замена коллекции является целью, предпочтительным вариантом разработки является включение метод для удаления всех элементов из коллекции, а также метод для повторного заполнения коллекции. В разделе <xref:System.Collections.ArrayList.Clear%2A> и <xref:System.Collections.ArrayList.AddRange%2A> методы <xref:System.Collections.ArrayList?displayProperty=fullName> класса, например, этот шаблон.

Двоичный файл и XML-сериализация поддерживает свойства только для чтения, которые относятся к коллекциям. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> Класс имеет особые требования для типов, реализующих <xref:System.Collections.ICollection> и <xref:System.Collections.IEnumerable?displayProperty=fullName> чтобы сериализоваться.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение данного правила, сделайте свойство только для чтения. Если это требуется для разработки, добавьте методы для очистки и повторного заполнения коллекции.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Не следует отключать предупреждения из этого правила.

## <a name="example"></a>Пример

В следующем примере показан тип со свойством коллекции, допускающее запись и показано, как коллекции может быть заменен напрямую. Кроме того, предпочтительный способ замены свойства только для чтения коллекцию с помощью `Clear` и `AddRange` показаны методы.

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Связанные правила

[CA1819: свойства не должны возвращать массивы](../code-quality/ca1819-properties-should-not-return-arrays.md)