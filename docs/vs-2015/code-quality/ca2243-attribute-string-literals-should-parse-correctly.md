---
title: 'CA2243: литералы строк атрибутов должны анализироваться правильно | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 62a2adc6f01e5cb26a6af26d71a124f8b81e07fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671966"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: синтаксический анализ строковых литералов атрибута должен осуществляться правильно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Параметр строкового литерала атрибута не анализируется правильно для URL-адреса, идентификатора GUID или версии.

## <a name="rule-description"></a>Описание правила
 Поскольку атрибуты являются производными от <xref:System.Attribute?displayProperty=fullName>, а атрибуты используются во время компиляции, в конструкторы могут передаваться только постоянные значения. Параметры атрибутов, которые должны представлять URL-адреса, GUID и версии, не могут быть типизированы как <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName> и <xref:System.Version?displayProperty=fullName>, так как эти типы не могут быть представлены как константы. Вместо этого они должны быть представлены строками.

 Поскольку параметр типизирован как строка, возможно, что параметр с неправильным форматом может быть передан во время компиляции.

 Это правило использует эвристику именования для поиска параметров, представляющих универсальный код ресурса (URI), глобальный уникальный идентификатор (GUID) или версию, и проверяет правильность переданного значения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Измените строку параметра на URL-адрес с правильным форматом, GUID или версию.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Если параметр не представляет URL-адрес, GUID или версию, можно отключить вывод предупреждения из этого правила.

## <a name="example"></a>Пример
 В следующем примере показан код для AssemblyFileVersionAttribute, нарушающего это правило.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 Правило активируется следующим образом:

- Параметры, содержащие "Version", и не могут быть проанализированы в System. Version.

- Параметры, содержащие "GUID", не могут быть проанализированы в System. GUID.

- Параметры, содержащие "URI", "urn" или "URL", и не могут быть проанализированы в System. URI.

## <a name="see-also"></a>См. также раздел
 [CA1054: параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
