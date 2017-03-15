---
title: "CA2227: свойства коллекции должны иметь параметр &quot;только для чтения&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
helpviewer_keywords: 
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA2227: свойства коллекции должны иметь параметр &quot;только для чтения&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CollectionPropertiesShouldBeReadOnly|  
|CheckId|CA2227|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Внешне видимое свойство, допускающее запись, является типом, реализующим <xref:System.Collections.ICollection?displayProperty=fullName>.  Массивы, индексы \(свойства с именем "Item"\) и наборы разрешений этим правилом не учитываются.  
  
## Описание правила  
 Свойство коллекции, допускающее запись, позволяет пользователю заменять коллекцию полностью другой коллекцией.  Свойство только для чтения предотвращает замену коллекции, но по\-прежнему допускает установку, настройку отдельных членов.  Если замена коллекции является целью, предпочтительным вариантом разработки будет включение метода для удаления всех элементов из коллекции, а также метода для повторного заполнения коллекции.  Пример такого шаблона см. в методах <xref:System.Collections.ArrayList.Clear%2A> и <xref:System.Collections.ArrayList.AddRange%2A> класса <xref:System.Collections.ArrayList?displayProperty=fullName>.  
  
 Как двоичная, так и XML\-сериализация поддерживает свойства только для чтения, являющиеся коллекциями.  Класс <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> предъявляет особые требования к типам, реализующим <xref:System.Collections.ICollection> и <xref:System.Collections.IEnumerable?displayProperty=fullName>, для выполнения сериализации.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, сделайте свойство доступным только для чтения и, если это требуется для разработки, добавьте методы для очистки и повторного заполнения коллекции.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показан тип со свойством коллекции, доступным для записи, и продемонстрирована непосредственная замена коллекции.  Также показан предпочтительный способ замены свойства коллекции только для чтения с помощью методов `Clear` и `AddRange`.  
  
 [!code-cs[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]  
  
## Связанные правила  
 [CA1819: свойства не должны возвращать массивы](../code-quality/ca1819-properties-should-not-return-arrays.md)