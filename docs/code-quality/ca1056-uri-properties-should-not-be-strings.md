---
title: CA1056. Свойства URI не должны быть строками
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 65c111e1379c3421f7541d05b817dd10be6bd674
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927523"
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056. Свойства URI не должны быть строками

|||
|-|-|
|TypeName|UriPropertiesShouldNotBeStrings|
|CheckId|CA1056|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип объявляет строковое свойство, имя которого содержит «uri», «Uri», «urn», «Urn», «url» или «Url».

## <a name="rule-description"></a>Описание правила
 Это правило разделяет имя свойства на токены, используя соглашения о регистре Pascal и проверяет, равно ли каждый токен «uri», «Uri», «urn», «Urn», «url» или «Url». Если есть совпадение имени, правиле предполагается, что свойство представляет универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. <xref:System.Uri?displayProperty=fullName> Класс предоставляет аналогичные услуги надежным и безопасным способом.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените значение свойства на <xref:System.Uri> типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если свойство не представляет URI.

## <a name="example"></a>Пример
 В следующем примере показано типом, `ErrorProne`, который нарушает это правило и тип, `SaferWay`, соответствующий этому правилу.

 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Связанные правила
 [CA1054: Параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI возвращать значения не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Передавайте объекты System.Uri вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: Строка URI вызывают перегрузки System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)