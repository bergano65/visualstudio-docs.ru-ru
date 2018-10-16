---
title: 'CA2227: свойства коллекции должны иметь параметр "только для чтения"'
ms.date: 09/28/2018
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
ms.openlocfilehash: f1bbd3e6ba97d969694e7d2142978c12552b3c50
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860255"
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

Свойство для записи коллекции позволяет пользователю заменять одну коллекцию совершенно другую коллекцию. Свойство только для чтения останавливает замену коллекции, но по-прежнему позволяет отдельных членов. Если замена коллекции является целью, предпочтительным вариантом разработки является включение метод, чтобы удалить все элементы из коллекции и метод для повторного заполнения коллекции. См. в разделе <xref:System.Collections.ArrayList.Clear%2A> и <xref:System.Collections.ArrayList.AddRange%2A> методы <xref:System.Collections.ArrayList?displayProperty=fullName> пример этого шаблона.

Как двоичная сериализация и сериализация XML поддерживают только для чтения свойства, которые представляют собой коллекции. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> Класс имеет особые требования для типов, реализующих <xref:System.Collections.ICollection> и <xref:System.Collections.IEnumerable?displayProperty=fullName> чтобы быть сериализуемым.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, сделайте свойство только для чтения. Если это требуется для разработки, добавьте методы для очистки и повторного заполнения коллекции.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Можно отключить предупреждение, если свойство является частью [объект передачи данных (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) класса.

В противном случае не следует отключать предупреждения из этого правила.

## <a name="example"></a>Пример

В следующем примере показан тип со свойством коллекции, допускающее запись и показано, как коллекции можно заменить напрямую. Кроме того, он показывает предпочтительный способ замены свойство только для чтения коллекцию с помощью `Clear` и `AddRange` методы.

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Связанные правила

- [CA1819: свойства не должны возвращать массивы](../code-quality/ca1819-properties-should-not-return-arrays.md)