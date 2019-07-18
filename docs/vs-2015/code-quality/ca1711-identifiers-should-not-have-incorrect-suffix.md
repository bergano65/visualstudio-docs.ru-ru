---
title: CA1711. Идентификаторы не должны иметь неверных суффиксов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c0ed08a50ce7e4c665839f6dccb4913e13d0d774
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65676471"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711. Идентификаторы не должны иметь неправильные суффиксы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

- делегат

- Enum

- Impl - вместо этого используйте «Core»

- Ex или подобный суффикс, чтобы отличить его от более ранней версии того же типа

  Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает обучения, необходимый для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите суффикс из имени типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Нельзя отключить предупреждение из этого правила, если суффикс не будет однозначен в домене приложения.

## <a name="related-rules"></a>Связанные правила
 [CA1710: Идентификаторы должны иметь правильные суффиксы](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>См. также
 [Атрибуты](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: События и делегаты](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
