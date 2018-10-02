---
title: 'CA2227: Свойства коллекции должны быть только для чтения | Документация Майкрософт'
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
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c9c91a0e563c7e83157dcff06e982c1bda40c5b5
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591222"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: свойства коллекции должны иметь параметр "только для чтения"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2227: свойства коллекции должны быть только для чтения](https://docs.microsoft.com/visualstudio/code-quality/ca2227-collection-properties-should-be-read-only).

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Категория|Microsoft.Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Свойство, которое доступного для записи — это тип, реализующий <xref:System.Collections.ICollection?displayProperty=fullName>. В правиле учитываются массивов, индексаторов (свойства с именем «Item») и наборы разрешений.

## <a name="rule-description"></a>Описание правила
 Свойство для записи коллекции позволяет пользователю заменять одну коллекцию совершенно другую коллекцию. Свойство только для чтения предотвращает замену коллекции, но по-прежнему допускает установку, настройку отдельных членов. Если замена коллекции является целью, предпочтительным вариантом разработки является включение метод для удаления всех элементов из коллекции, а также способ повторного заполнения коллекции. См. в разделе <xref:System.Collections.ArrayList.Clear%2A> и <xref:System.Collections.ArrayList.AddRange%2A> методы <xref:System.Collections.ArrayList?displayProperty=fullName> пример этого шаблона.

 Как двоичная сериализация и сериализация XML поддерживают только для чтения свойства, которые представляют собой коллекции. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> Класс имеет особые требования для типов, реализующих <xref:System.Collections.ICollection> и <xref:System.Collections.IEnumerable?displayProperty=fullName> чтобы быть сериализуемым.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделать свойство доступным только для чтения и, если это требуется для разработки, добавьте методы для очистки и повторного заполнения коллекции.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан тип со свойством коллекции, допускающее запись и показано, как коллекции можно заменить напрямую. Кроме того, предпочтительный способ замены свойство только для чтения коллекцию с помощью `Clear` и `AddRange` методы показаны.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1819: свойства не должны возвращать массивы](../code-quality/ca1819-properties-should-not-return-arrays.md)



