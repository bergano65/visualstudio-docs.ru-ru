---
title: CA1057. Строка URI вызывают перегрузки System.Uri | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4cf50ca225544b06409415320c73e7824a10843a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991089"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057. Перегрузки строковых параметров URI вызывают перегрузки System.Uri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип объявляет перегрузки метода, которые отличаются только заменой строкового параметра с <xref:System.Uri?displayProperty=fullName> перегрузка, которая принимает строковый параметр и параметр не вызывает перегрузку, принимающую <xref:System.Uri> параметра.

## <a name="rule-description"></a>Описание правила
 Поскольку перегрузки отличаются только по строке /<xref:System.Uri> параметра, подразумевается, что для представления универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. <xref:System.Uri> Класс предоставляет аналогичные услуги надежным и безопасным способом. Чтобы пользоваться всеми преимуществами <xref:System.Uri> класса, при перегрузке строки следует вызывать <xref:System.Uri> перегрузки, используя строковый аргумент.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Повторно реализовать метод, который используется строковое представление URI, поэтому он создает экземпляр класса <xref:System.Uri> класса, используя строковый аргумент, а затем передает <xref:System.Uri> объект перегрузку, которая имеет <xref:System.Uri> параметра.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если параметр строки не представляет URI.

## <a name="example"></a>Пример
 В следующем примере показано правильно реализованный перегружающий.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2234: Передавайте объекты System.Uri вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: Свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI возвращать значения не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
