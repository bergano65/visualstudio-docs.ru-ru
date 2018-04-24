---
title: 'CA2243: синтаксический анализ строковых литералов атрибута должен осуществляться правильно'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fcfb3d3ce0709f95ff864d081ba90c2aa49fad15
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: синтаксический анализ строковых литералов атрибута должен осуществляться правильно
|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Атрибут строкового литерала не интерпретирует для URL-адрес, идентификатор GUID или версии.

## <a name="rule-description"></a>Описание правила
 Поскольку атрибуты являются производными от <xref:System.Attribute?displayProperty=fullName>, а атрибуты используются во время компиляции, их конструкторы могут передаваться только константные значения. Параметры атрибутов, которые должны представлять URL-адреса, идентификаторы GUID или версии не могут иметь тип <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, и <xref:System.Version?displayProperty=fullName>, так как эти типы не могут быть представлены как константы. Вместо этого они должны быть представлены строками.

 Поскольку параметр вводится как строка, существует возможность, что во время компиляции может быть передан параметр неправильного формата.

 Это правило использует эвристику именования для поиска параметров, которые представляют универсальный код ресурса (URI), глобально уникальный идентификатор (GUID) или версии и проверяет правильность переданному значению.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Замените строку параметра правильно сформированный URL-адрес, идентификатор GUID или версии.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить предупреждение из этого правила, если параметр не представляет URL-адрес, идентификатор GUID или версии.

## <a name="example"></a>Пример
 В следующем примере показан код для AssemblyFileVersionAttribute, нарушающий это правило.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

 Правило срабатывает, следующие:

-   Параметры, содержащие «version» и не может быть проанализирован для System.Version.

-   Параметры, содержащие «guid» и не может быть проанализирован для System.Guid.

-   Параметры, содержащие «uri», «urn» или «url» и не может быть проанализировано на System.Uri.

## <a name="see-also"></a>См. также
 [CA1054: параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)