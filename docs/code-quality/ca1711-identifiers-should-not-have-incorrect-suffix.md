---
title: CA1711. Идентификаторы не должны иметь неправильные суффиксы
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a612aa39899336eda4802e849529ae61faf192be
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54935648"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711. Идентификаторы не должны иметь неправильные суффиксы

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Идентификатор имеет неверный суффикс.

## <a name="rule-description"></a>Описание правила

По соглашению только имена типов, расширяющих определенные базовые типы или реализующих определенные интерфейсы, а также типы, производные от этих типов должно заканчиваться определенные зарезервированные суффиксы. В именах других типов зарезервированные суффиксы использоваться не должны.

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

Кроме того, следующие суффиксы должны **не** использоваться:

- `Delegate`

- `Enum`

- `Impl` (используйте `Core` вместо)

- `Ex` или же суффикс, чтобы отличить его от более ранней версии того же типа

Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает обучения, необходимый для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Удалите суффикс из имени типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Нельзя отключить предупреждение из этого правила, если суффикс не будет однозначен в домене приложения.

## <a name="related-rules"></a>Связанные правила

- [CA1710: Идентификаторы должны иметь правильные суффиксы](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>См. также

- [Атрибуты](/dotnet/standard/design-guidelines/attributes)
- [Обработка и вызов событий](/dotnet/standard/events/index)