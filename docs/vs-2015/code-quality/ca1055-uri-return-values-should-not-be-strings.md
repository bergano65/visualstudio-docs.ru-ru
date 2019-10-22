---
title: 'CA1055: возвращаемые значения URI не должны быть строками | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1817d8aa51f1e47e23a7b5ee79580c44f3fe521f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603228"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055: возвращаемые значения URI не должны быть строками
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя метода содержит "URI", "URI", "urn", "urn", "URL" или "URL", а метод возвращает строку.

## <a name="rule-description"></a>Описание правила
 Это правило разбивает имя метода на токены на основе соглашения об использовании регистра Pascal и проверяет, равны ли каждый маркер URI, URI, URN, URN, "URL" или "URL". При наличии совпадения правило предполагает, что метод возвращает универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. Класс <xref:System.Uri?displayProperty=fullName> предоставляет эти службы безопасным и безопасным способом.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените тип возвращаемого значения на <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если возвращаемое значение не представляет URI.

## <a name="example"></a>Пример
 В следующем примере показан тип, `ErrorProne`, который нарушает данное правило, и тип `SaferWay`, удовлетворяющий правилу.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1056: свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA2234: передавайте объекты System.Uri вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: перегрузки строковых параметров URI вызывают перегрузки System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
