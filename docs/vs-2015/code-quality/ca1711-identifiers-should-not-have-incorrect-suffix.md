---
title: 'CA1711: идентификаторы не должны иметь неверные суффиксы | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f59a1c88701cf132a46c66eb6550f03eb870d63d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669178"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711: идентификаторы не должны иметь неверных суффиксов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Идентификатор имеет неверный суффикс.

## <a name="rule-description"></a>Описание правила
 По соглашению имена типов, которые расширяют определенные базовые типы или реализуют определенные интерфейсы или типы, производные от этих типов, должны заканчиваться определенными зарезервированными суффиксами. В именах других типов зарезервированные суффиксы использоваться не должны.

 В следующей таблице перечислены зарезервированные суффиксы и базовые типы и интерфейсы, с которыми они связаны.

|Суффикс|Базовый тип или интерфейс|
|------------|--------------------------|
|Атрибут|<xref:System.Attribute?displayProperty=fullName>|
|Collection|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|Словарь|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|EventHandler|Делегат обработчика событий|
|Исключение|<xref:System.Exception?displayProperty=fullName>|
|Разрешение|<xref:System.Security.IPermission?displayProperty=fullName>|
|Queue|<xref:System.Collections.Queue?displayProperty=fullName>|
|Стек|<xref:System.Collections.Stack?displayProperty=fullName>|
|Поток|<xref:System.IO.Stream?displayProperty=fullName>|

 Кроме того, **не** следует использовать следующие суффиксы:

- делегат

- Enum

- Impl — используйте вместо него "Core"

- Ex или аналогичный суффикс, чтобы отличить его от более ранней версии того же типа

  Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает кривую обучения, необходимую для новых библиотек программного обеспечения, и повышает уверенность пользователей в том, что библиотека была разработана кем-то, кто имеет опыт разработки управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите суффикс из имени типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Нельзя отключить предупреждение из этого правила, если суффикс не будет однозначен в домене приложения.

## <a name="related-rules"></a>Связанные правила
 [CA1710: идентификаторы должны иметь правильные суффиксы](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>См. также раздел
 [Атрибуты](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: события и делегаты](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
