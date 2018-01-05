---
title: "CA2227: Свойства коллекции должны быть только для чтения | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8a1835c5e600320ec8b36102e4749d92cf21eae1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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