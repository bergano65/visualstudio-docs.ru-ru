---
title: CA1058. Типы не должны расширять определенные базовые типы
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa1ffbb393700647f12c455c8d1307a77548f2d1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235496"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058. Типы не должны расширять определенные базовые типы

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Тип расширяет один из следующих базовых типов:

- <xref:System.ApplicationException?displayProperty=fullName>
- <xref:System.Xml.XmlDocument?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.Queue?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
- <xref:System.Collections.SortedList?displayProperty=fullName>
- <xref:System.Collections.Stack?displayProperty=fullName>

По умолчанию это правило рассматривает только видимые извне типы, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Исключения должны быть производными <xref:System.Exception?displayProperty=fullName> от или одного из его подклассов <xref:System> в пространстве имен.

Не создавайте подкласс класса <xref:System.Xml.XmlDocument> , если необходимо создать XML-представление базовой объектной модели или источника данных.

### <a name="non-generic-collections"></a>Неуниверсальные коллекции

По возможности используйте и (или) расширьте универсальные коллекции. Не расширяйте неуниверсальные коллекции в коде, пока вы не отгрузили ее ранее.

**Примеры неправильного использования**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

**Примеры правильного использования**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, необходимо создать производный тип от другого базового типа или универсальной коллекции.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Не отключайте предупреждение о нарушении этого правила о <xref:System.ApplicationException>нарушениях. В этом правиле можно отключить вывод предупреждений о <xref:System.Xml.XmlDocument>нарушениях. Можно спокойно отключить предупреждение о неуниверсальной коллекции, если код был выпущен ранее.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca1058.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (конструктор). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).