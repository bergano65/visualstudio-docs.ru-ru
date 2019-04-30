---
title: CA1708. Идентификаторы должны отличаться не только прописными и строчными буквами
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32ac2e430abdc068070457dcf362e39dcbc0b398
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797556"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708. Идентификаторы должны отличаться не только прописными и строчными буквами

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Имена двух типов, членов, параметров или полное имя пространства имен идентичны, при преобразовании в нижний регистр.

По умолчанию это правило считывает только типы, видимые извне, члены и пространства имен, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Идентификаторы пространств имен, типов, членов и параметров не могут отличаться только регистром знаков, поскольку языки программирования, поддерживаемые средой CLR, не обязательно учитывают регистр знаков. Например [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] — это широко используемый язык, без учета регистра.

Это правило срабатывает на только открытые члены.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Выберите имя, которое является уникальным, при сравнении с другими идентификаторами без учета регистра.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует. Библиотека может стать недоступной в некоторых языках платформы .NET Framework.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```
dotnet_code_quality.ca1708.api_surface = private, internal
```

Этот параметр для только что это правило, для всех правил или для всех правил можно настроить в этой категории (именования). Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Пример нарушения

В следующем примере показано нарушение этого правила.

[!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)