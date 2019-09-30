---
title: CA2234. Передавайте объекты System.Uri вместо строк
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b52d98716a774c05ca085e2b7023a5d1faa69baa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237966"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234. Передавайте объекты System.Uri вместо строк

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Выполняется вызов метода, имеющего строковый параметр, имя которого содержит "URI", "URI", "urn", "urn", "URL" или "URL", а объявляющий тип метода содержит соответствующую перегрузку метода, имеющую <xref:System.Uri?displayProperty=fullName> параметр.

По умолчанию это правило рассматривает только видимые извне методы и типы, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Имя параметра разбивается на маркеры в соответствии с соглашением о регистрах Camel, а затем каждый маркер проверяется на равенство "URI", "URI", "urn", "urn", "URL" или "URL". При совпадении предполагается, что параметр представляет универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. <xref:System.Uri> Класс предоставляет эти службы безопасным и безопасным способом. Если существует выбор между двумя перегрузками, которые отличаются только представлением URI, пользователь должен выбрать перегрузку, которая принимает <xref:System.Uri> аргумент.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, вызовите перегрузку, которая принимает <xref:System.Uri> аргумент.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Можно отключить вывод предупреждения из этого правила, если строковый параметр не представляет URI.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca2234.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (использование). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере показан метод, `ErrorProne`, который нарушает правило и `SaferWay`метод, который правильно вызывает <xref:System.Uri> перегрузку:

[!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
[!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
[!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA1057 Перегрузки строковых URI вызывают перегрузки System. URI](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
- [CA1056: Свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054: Параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA1055: Возвращаемые значения URI не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)