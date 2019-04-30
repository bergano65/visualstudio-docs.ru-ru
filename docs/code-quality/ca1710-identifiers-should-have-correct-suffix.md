---
title: CA1710. Идентификаторы должны иметь правильные суффиксы
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65ac417476752da832e5e9ebe693f6c83a5c1cfe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797418"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710. Идентификаторы должны иметь правильные суффиксы

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Идентификатор не иметь правильные суффиксы.

По умолчанию это правило считывает только видимое извне идентификаторов, но это [можно настроить](#configurability).

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

Типы, реализующие <xref:System.Collections.ICollection> и коллекцию определенных элементов имеют имена со словом «Collection». Например, коллекция <xref:System.Collections.Queue> объектов будет иметь имя «QueueCollection». Суффикс «Collection» означает, что элементы коллекции могут быть перечислены с помощью `foreach` (`For Each` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) инструкции.

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

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```
dotnet_code_quality.ca1710.api_surface = private, internal
```

Этот параметр для только что это правило, для всех правил или для всех правил можно настроить в этой категории (именования). Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Связанные правила

[CA1711: Идентификаторы не должны иметь неверных суффиксов](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>См. также

- [Атрибуты](/dotnet/standard/design-guidelines/attributes)
- [Обработка и вызов событий](/dotnet/standard/events/index)