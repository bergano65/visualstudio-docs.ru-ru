---
title: 'CA1710: Идентификаторы должны иметь правильные суффиксы | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2256e3f20dfdb4ddb8efa28d7ecdd203a139bcc5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940168"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: идентификаторы должны иметь правильные суффиксы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Идентификатор не иметь правильные суффиксы.

## <a name="rule-description"></a>Описание правила
 По правилам имена типов, расширяющих определенные базовые типы или реализующих определенные интерфейсы, а также типы, производные от этих типов имеют суффикс, связанный с базовым типом или интерфейсом.

 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает обучения, необходимый для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

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

 Типы, реализующие <xref:System.Collections.ICollection> и обобщенный тип структуры данных, такие как словарь, стек или очереди, допускаются имена, которые предоставляют понятные сведения об предполагаемое использование типа.

 Типы, реализующие <xref:System.Collections.ICollection> и коллекцию определенных элементов имеют имена со словом «Collection». Например, коллекция <xref:System.Collections.Queue> объектов будет иметь имя «QueueCollection». Суффикс «Collection» означает, что элементы коллекции могут быть перечислены с помощью `foreach` (`For Each` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) инструкции.

 Типы, реализующие <xref:System.Collections.IDictionary> имена которых заканчиваются словом «Словарь», даже если тип также реализует <xref:System.Collections.IEnumerable> или <xref:System.Collections.ICollection>. Соглашения об именах суффикс «Collection» и «Словарь» позволяют пользователям различать два шаблона перечисления.

 Типы с суффиксом «Collection» следовать этому шаблону перечисления.

```
foreach(SomeType x in SomeCollection) { }
```

 Типы с суффиксом «Словарь» следовать этому шаблону перечисления.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 Объект <xref:System.Data.DataSet> объект представляет собой коллекцию из <xref:System.Data.DataTable> объекты, которые состоят из наборов <xref:System.Data.DataColumn?displayProperty=fullName> и <xref:System.Data.DataRow?displayProperty=fullName> objects, наряду с другими пользователями. Эти коллекции реализуют <xref:System.Collections.ICollection> через базовый <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> класса.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Переименуйте тип таким образом, чтобы он имел правильный термин.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение, используйте суффикс «Collection», если тип является структурой обобщенных данных, которую можно расширить или который будет содержать произвольный набор различных элементов. В этом случае имя, которое предоставляет важную информацию о реализации, производительности или других характеристик структуры данных может оказаться целесообразным (например, BinaryTree). В случаях, когда тип представляет коллекцию определенного типа (например, StringCollection), не отключайте предупреждение из этого правила, так как суффикс указывает, что тип может быть перечислены с помощью `foreach` инструкции.

 Для других суффиксов не отключайте предупреждение из этого правила. Суффикс позволяет быть очевидно из имени типа.

## <a name="related-rules"></a>Связанные правила
 [CA1711: идентификаторы не должны иметь неверных суффиксов](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>См. также
 [Атрибуты](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: события и делегаты](http://msdn.microsoft.com/en-us/d98fd58b-fa4f-4598-8378-addf4355a115)



