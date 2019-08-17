---
title: CA1056. Свойства URI не должны быть строками
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2d9ff79bc7e276e4070a1df1760c0cfde7ed28b1
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547351"
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056. Свойства URI не должны быть строками

|||
|-|-|
|TypeName|UriPropertiesShouldNotBeStrings|
|CheckId|CA1056|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Тип объявляет строковое свойство, имя которого содержит "URI", "URI", "urn", "urn", "URL" или "URL".

По умолчанию это правило рассматривает только видимые извне типы, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Это правило разбивает имя свойства на токены на основе соглашения об использовании регистра Pascal и проверяет, равны ли каждый маркер URI, URI, URN, URN, "URL" или "URL". При наличии совпадения правило предполагает, что свойство представляет универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. <xref:System.Uri?displayProperty=fullName> Класс предоставляет эти службы безопасным и безопасным способом.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, измените свойство на <xref:System.Uri> тип.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Можно отключить вывод предупреждения из этого правила, если свойство не представляет URI.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca1056.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (конструктор). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере показан тип, `ErrorProne`, который нарушает данное правило, и тип, `SaferWay`который удовлетворяет правилу.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Связанные правила

- [CA1054: Параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA1055: Возвращаемые значения URI не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
- [CA2234 Передавать объекты System. URI вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057 Перегрузки строковых URI вызывают перегрузки System. URI](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)