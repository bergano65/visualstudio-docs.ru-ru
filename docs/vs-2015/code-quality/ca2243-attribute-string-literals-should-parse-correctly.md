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
ms.openlocfilehash: 09e932651576f9b6d595657ad024b8f2697ad016
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535750"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243. Синтаксический разбор строковых литералов должен осуществляться правильно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Параметр строкового литерала атрибута не анализируется правильно для URL-адреса, идентификатора GUID или версии.

## <a name="rule-description"></a>Описание правила
 Поскольку атрибуты являются производными от <xref:System.Attribute?displayProperty=fullName> , а атрибуты используются во время компиляции, в конструкторы могут передаваться только постоянные значения. Параметры атрибутов, которые должны представлять URL-адреса, GUID и версии, не могут быть типизированы как <xref:System.Uri?displayProperty=fullName> , <xref:System.Guid?displayProperty=fullName> и <xref:System.Version?displayProperty=fullName> , так как эти типы не могут быть представлены как константы. Вместо этого они должны быть представлены строками.

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

## <a name="see-also"></a>См. также:
 [CA1054. Параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
