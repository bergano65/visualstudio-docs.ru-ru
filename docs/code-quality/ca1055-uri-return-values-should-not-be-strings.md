---
title: CA1055. Возвращаемые значения URI не должны быть строками
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4517fc0d0dbfedc59a5a621f894d7e1d77b35c38
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842173"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055. Возвращаемые значения URI не должны быть строками

|||
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Имя метода содержит «uri», «Uri», «urn», «Urn», «url» или «Url», и метод возвращает строку.

По умолчанию это правило считывает только открытые методы, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Это правило разделяет имя метода на токены, используя соглашения о регистре Pascal и проверяет, равно ли каждый токен «uri», «Uri», «urn», «Urn», «url» или «Url». Если есть совпадение имени, правиле предполагается, что метод возвращает универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. <xref:System.Uri?displayProperty=fullName> Класс предоставляет аналогичные услуги надежным и безопасным способом.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, измените тип возвращаемого значения на <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила, если возвращаемое значение не представляет URI.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```ini
dotnet_code_quality.ca1055.api_surface = private, internal
```

В этой категории (структуры) можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере показано типом, `ErrorProne`, который нарушает это правило и тип, `SaferWay`, соответствующий этому правилу.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Связанные правила

- [CA1056: Свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054: Параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA2234: Передавайте объекты System.Uri вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057: Строка URI вызывают перегрузки System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)