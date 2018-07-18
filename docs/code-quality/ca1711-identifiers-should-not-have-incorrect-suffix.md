---
title: 'CA1711: идентификаторы не должны иметь неверных суффиксов'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4faed3f5d49c6c08ca0a9bc90465f4e21ef3fec8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916963"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711: идентификаторы не должны иметь неверных суффиксов
|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Идентификатор имеет неверный суффикс.

## <a name="rule-description"></a>Описание правила
 По соглашению определенные зарезервированные суффиксы должны добавляться только имена типов, расширяющих определенные базовые типы или реализуют определенные интерфейсы, а также типы, производные от этих типов. В именах других типов зарезервированные суффиксы использоваться не должны.

 В следующей таблице перечислены зарезервированные суффиксы и базовые типы и интерфейсы, с которыми они связаны.

|Суффикс|Базовый тип или интерфейс|
|------------|--------------------------|
|Атрибут|<xref:System.Attribute?displayProperty=fullName>|
|Коллекция|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|Словарь|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|Обработчик событий|Делегат обработчика событий|
|Исключение|<xref:System.Exception?displayProperty=fullName>|
|Разрешение|<xref:System.Security.IPermission?displayProperty=fullName>|
|Queue|<xref:System.Collections.Queue?displayProperty=fullName>|
|Стек|<xref:System.Collections.Stack?displayProperty=fullName>|
|Поток|<xref:System.IO.Stream?displayProperty=fullName>|

 Кроме того, следующие суффиксы следует **не** использоваться:

-   делегат

-   Enum

-   Impl - вместо этого используйте «Core»

-   Ex или подобный суффикс, чтобы отличить его от более ранней версии того же типа

 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных общеязыковая среда выполнения. Это уменьшает обучения, необходимое для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана с тем, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите суффикс из имени типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Нельзя отключить предупреждение из этого правила, если суффикс не будет однозначен в домене приложения.

## <a name="related-rules"></a>Связанные правила
 [CA1710: идентификаторы должны иметь правильные суффиксы](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>См. также
 [Атрибуты](/dotnet/standard/design-guidelines/attributes) [обработка и вызов событий](/dotnet/standard/events/index)