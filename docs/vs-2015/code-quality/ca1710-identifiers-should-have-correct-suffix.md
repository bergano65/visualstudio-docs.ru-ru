---
title: 'CA1710: идентификаторы должны иметь правильные суффиксы | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7dc0ed72ddab39bda5f3de9b978f4d55dc2358ba
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669168"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: идентификаторы должны иметь правильные суффиксы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Идентификатор имеет неправильный суффикс.

## <a name="rule-description"></a>Описание правила
 По соглашению имена типов, которые расширяют определенные базовые типы или реализуют определенные интерфейсы, или типы, производные от этих типов, имеют суффикс, связанный с базовым типом или интерфейсом.

 Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает кривую обучения, необходимую для новых библиотек программного обеспечения, и повышает уверенность пользователей в том, что библиотека была разработана кем-то, кто имеет опыт разработки управляемого кода.

 В следующей таблице перечислены базовые типы и интерфейсы, имеющие связанные суффиксы.

|Базовый тип или интерфейс|Суффикс|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Атрибут|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Исключение|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Collection|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Словарь|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Collection|
|<xref:System.Collections.Queue?displayProperty=fullName>|Коллекция или очередь|
|<xref:System.Collections.Stack?displayProperty=fullName>|Коллекция или стек|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Collection|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Словарь|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Коллекция или DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Поток|
|<xref:System.Security.IPermission?displayProperty=fullName>|Разрешение|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Условие|
|Делегат обработчика событий.|EventHandler|

 Типы, реализующие <xref:System.Collections.ICollection> и являются обобщенным типом структуры данных, например словарем, стеком или очередью, допускаются имена, которые предоставляют осмысленные сведения о предполагаемом использовании типа.

 Типы, реализующие <xref:System.Collections.ICollection> и являются коллекцией конкретных элементов, имеют имена, заканчивающиеся словом "Collection". Например, коллекция объектов <xref:System.Collections.Queue> будет иметь имя «Куеуеколлектион». Суффикс Collection означает, что члены коллекции можно перечислить с помощью оператора `foreach` (`For Each` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

 Типы, реализующие <xref:System.Collections.IDictionary>, имеют имена, заканчивающиеся словом "Dictionary", даже если тип также реализует <xref:System.Collections.IEnumerable> или <xref:System.Collections.ICollection>. Соглашения об именовании суффиксов "Collection" и "Dictionary" позволяют пользователям различать следующие два шаблона перечисления.

 Типы с суффиксом "Collection" следуют этому шаблону перечисления.

```
foreach(SomeType x in SomeCollection) { }
```

 Типы с суффиксом "Dictionary" следуют этому шаблону перечисления.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 Объект <xref:System.Data.DataSet> состоит из коллекции объектов <xref:System.Data.DataTable>, которые состоят из коллекций объектов <xref:System.Data.DataColumn?displayProperty=fullName> и <xref:System.Data.DataRow?displayProperty=fullName>, в других случаях. Эти коллекции реализуют <xref:System.Collections.ICollection> через базовый класс <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Переименуйте тип так, чтобы он был суффиксом с правильным термином.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно спокойно отключить предупреждение, чтобы использовать суффикс "Collection", если тип представляет собой обобщенную структуру данных, которая может быть расширена или будет содержать произвольный набор различных элементов. В этом случае имя, которое предоставляет осмысленные сведения о реализации, производительности или других характеристиках структуры данных, может быть осмысленным (например, Бинаритри). В случаях, когда тип представляет коллекцию определенного типа (например, StringCollection), не следует отключать предупреждение из этого правила, так как суффикс указывает, что тип можно перечислить с помощью инструкции `foreach`.

 Для других суффиксов не следует отключать предупреждение из этого правила. Суффикс позволяет очевидное использование из имени типа.

## <a name="related-rules"></a>Связанные правила
 [CA1711: идентификаторы не должны иметь неверных суффиксов](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>См. также раздел
 [Атрибуты](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: события и делегаты](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
