---
title: "CA1710: Идентификаторы должны иметь правильные суффиксы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4fd4f23ab77e2b810d5064bd45e9f7d530e9844e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: идентификаторы должны иметь правильные суффиксы
|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectSuffix|  
|CheckId|CA1710|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Идентификатор не имеет правильного суффикса.  
  
## <a name="rule-description"></a>Описание правила  
 По правилам имена типов, расширяющих определенные базовые типы или реализуют определенные интерфейсы, а также типы, производные от этих типов имеют суффикс, связанный с базовым типом или интерфейсом.  
  
 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных общеязыковая среда выполнения. Это уменьшает обучения, необходимое для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана с тем, кто имеет опыт в разработке управляемого кода.  
  
 В следующей таблице перечислены базовые типы и интерфейсы, которые имеют связанные суффиксы.  
  
|Базовый тип или интерфейс|Суффикс|  
|--------------------------|------------|  
|<xref:System.Attribute?displayProperty=fullName>|Атрибут|  
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|  
|<xref:System.Exception?displayProperty=fullName>|Исключение|  
|<xref:System.Collections.ICollection?displayProperty=fullName>|Коллекция|  
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Словарь|  
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Коллекция|  
|<xref:System.Collections.Queue?displayProperty=fullName>|Коллекции или очереди|  
|<xref:System.Collections.Stack?displayProperty=fullName>|Коллекции или стека|  
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Коллекция|  
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Словарь|  
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|  
|<xref:System.Data.DataTable?displayProperty=fullName>|Коллекции или DataTable|  
|<xref:System.IO.Stream?displayProperty=fullName>|Поток|  
|<xref:System.Security.IPermission?displayProperty=fullName>|Разрешение|  
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Условие|  
|Делегат обработчика событий.|Обработчик событий|  
  
 Типы, реализующие <xref:System.Collections.ICollection> и являющиеся обобщенным типом структуры данных, такие как словарь, стек или очереди, допускаются имена, предоставляющую достоверных данных о предполагаемое использование типа.  
  
 Типы, реализующие <xref:System.Collections.ICollection> и коллекцию определенных элементов, имеют имена, которые заканчиваются словом «Collection». Например, коллекцию <xref:System.Collections.Queue> объектов будет иметь имя «QueueCollection». Суффикс «Collection» означает, что элементы коллекции могут быть перечислены с помощью `foreach` (`For Each` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) инструкции.  
  
 Типы, реализующие <xref:System.Collections.IDictionary> имена которых заканчиваются словом «Словарь», даже если тип также реализует <xref:System.Collections.IEnumerable> или <xref:System.Collections.ICollection>. Соглашения об именовании суффиксом «Collection» и «Dictionary» позволяют пользователям различать два шаблона перечисления.  
  
 Типы с суффиксом «Collection» следовать этому шаблону перечисления.  
  
```  
foreach(SomeType x in SomeCollection) { }  
```  
  
 Типы с суффиксом «Словарь» следовать этому шаблону перечисления.  
  
```  
foreach(SomeType x in SomeDictionary.Values) { }  
```  
  
 Объект <xref:System.Data.DataSet> объект содержит коллекцию <xref:System.Data.DataTable> объектов, состоящих из коллекции <xref:System.Data.DataColumn?displayProperty=fullName> и <xref:System.Data.DataRow?displayProperty=fullName> среди других объектов. Эти коллекции реализуют <xref:System.Collections.ICollection> через базовый <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> класса.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Переименуйте тип так, чтобы он имел правильный суффикс.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Его можно безопасно подавить предупреждение, используйте суффикс «Collection», если тип представляет собой обобщенную структуру данных, можно расширить, или который будет содержать произвольный набор различных элементов. В этом случае имя, которое предоставляет важную информацию о реализации, производительности или других характеристик структуры данных может иметь смысл (например, BinaryTree). В случаях, когда тип представляет коллекцию определенного типа (например, StringCollection), не отключайте предупреждение из этого правила, так как суффикс указывает, что тип может быть перечислены с помощью `foreach` инструкции.  
  
 Не отключайте предупреждение из этого правила для других суффиксов. Суффикс позволяет предполагаемого использования быть видно из имени типа.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1711: идентификаторы не должны иметь неверных суффиксов](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)  
  
## <a name="see-also"></a>См. также  
 [Атрибуты](/dotnet/standard/design-guidelines/attributes)   
 [Обработка и вызов событий](/dotnet/standard/events/index)  