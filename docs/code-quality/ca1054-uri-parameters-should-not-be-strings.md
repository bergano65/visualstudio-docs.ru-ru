---
title: CA1054. Параметры URI не должны быть строками
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 03d850eeb668f6c2b47d663b55e5461cabf9cbbf
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867465"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054. Параметры URI не должны быть строками

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Тип объявляет метод со строковым параметром, имя которого содержит «uri», «Uri», «urn», «Urn», «url» или «Url» и тип не объявляет соответствующую перегрузку, которая принимает <xref:System.Uri?displayProperty=fullName> параметра.

По умолчанию это правило считывает только типы, видимые извне, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Это правило разбивает имя параметра в токены, основывается на соглашении смешанный регистр знаков и проверяет, равно ли каждый токен «uri», «Uri», «urn», «Urn», «url» или «Url». Если есть совпадение имени, правиле предполагается, что параметр представляет универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. Если метод принимает строковое представление URI, соответствующую перегрузку должны быть предоставлены, принимающий экземпляр <xref:System.Uri> класс, который предоставляет аналогичные услуги надежным и безопасным способом.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, изменение параметра для <xref:System.Uri> введите; это является критическим изменением. Кроме того, обеспечьте перегрузку метода, принимающую <xref:System.Uri> параметр; это не критическое изменение.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила, если параметр не представляет URI.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```
dotnet_code_quality.ca1054.api_surface = private, internal
```

В этой категории (структуры) можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере показано типом, `ErrorProne`, который нарушает это правило и тип, `SaferWay`, соответствующий этому правилу.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Связанные правила

- [CA1056: Свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1055: URI возвращать значения не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
- [CA2234: Передавайте объекты System.Uri вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057: Строка URI вызывают перегрузки System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)