---
title: CA2243. Синтаксический разбор строковых литералов должен осуществляться правильно
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c0f078c21de023b1f5cfacde0cf122c179adb2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919902"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243. Синтаксический разбор строковых литералов должен осуществляться правильно

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Параметр строкового литерала атрибута не анализируется правильно для URL-адреса, идентификатора GUID или версии.

## <a name="rule-description"></a>Описание правила
Поскольку атрибуты являются производными <xref:System.Attribute?displayProperty=fullName>от, а атрибуты используются во время компиляции, в конструкторы могут передаваться только постоянные значения. Параметры атрибутов, которые должны представлять URL-адреса, GUID и версии, не могут <xref:System.Uri?displayProperty=fullName>быть <xref:System.Guid?displayProperty=fullName>типизированы <xref:System.Version?displayProperty=fullName>как, и, так как эти типы не могут быть представлены как константы. Вместо этого они должны быть представлены строками.

Поскольку параметр типизирован как строка, возможно, что параметр с неправильным форматом может быть передан во время компиляции.

Это правило использует эвристику именования для поиска параметров, представляющих универсальный код ресурса (URI), глобальный уникальный идентификатор (GUID) или версию, и проверяет правильность переданного значения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Измените строку параметра на URL-адрес с правильным форматом, GUID или версию.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Если параметр не представляет URL-адрес, GUID или версию, можно отключить вывод предупреждения из этого правила.

## <a name="example"></a>Пример
В следующем примере показан код для AssemblyFileVersionAttribute, нарушающего это правило.

[!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

Правило активируется следующими параметрами:

- Параметры, содержащие "Version", и не могут быть проанализированы в System. Version.

- Параметры, содержащие "GUID", не могут быть проанализированы в System. GUID.

- Параметры, содержащие "URI", "urn" или "URL", и не могут быть проанализированы в System. URI.

## <a name="see-also"></a>См. также

- [CA1054: Параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)