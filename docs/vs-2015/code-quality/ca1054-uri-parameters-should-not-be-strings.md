---
title: 'CA1054: Параметры URI не должны быть строками | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2062c7518545300074a0377b7a9cca7ddf1a8aa5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603370"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: параметры URI не должны быть строками
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип объявляет метод со строковым параметром, имя которого содержит "URI", "URI", "urn", "urn", "URL" или "URL", а тип не объявляет соответствующую перегрузку, которая принимает параметр <xref:System.Uri?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Это правило разбивает имя параметра на токены на основе соглашения о регистре Camel и проверяет, равны ли они URI, URI, URN, URN или URL-адрес. При наличии совпадения правило предполагает, что параметр представляет универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. Если метод принимает строковое представление URI, следует указать соответствующую перегрузку, которая принимает экземпляр класса <xref:System.Uri>, который предоставляет эти службы безопасным и безопасным способом.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените параметр на тип <xref:System.Uri>. Это критическое изменение. Кроме того, можно предоставить перегрузку метода, который принимает <xref:System.Uri> параметр; это неразрывное изменение.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Если параметр не представляет URI, можно отключить вывод предупреждения из этого правила.

## <a name="example"></a>Пример
 В следующем примере показан тип, `ErrorProne`, который нарушает данное правило, и тип `SaferWay`, удовлетворяющий правилу.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1056: свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055: возвращаемые значения URI не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: передавайте объекты System.Uri вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: перегрузки строковых параметров URI вызывают перегрузки System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
