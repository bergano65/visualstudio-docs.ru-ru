---
title: CA1057. Перегрузки строковых параметров URI вызывают перегрузки System.Uri
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cd22a228f0963e2bdc87df284402d119a0353c68
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922538"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057. Перегрузки строковых параметров URI вызывают перегрузки System.Uri

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип объявляет перегрузки метода, которые отличаются только заменой строкового параметра с <xref:System.Uri?displayProperty=fullName> перегрузка, которая принимает строковый параметр и параметр не вызывает перегрузку, принимающую <xref:System.Uri> параметра.

## <a name="rule-description"></a>Описание правила
 Поскольку перегрузки отличаются только по строке или <xref:System.Uri> параметра, подразумевается, что для представления универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. <xref:System.Uri> Класс предоставляет аналогичные услуги надежным и безопасным способом. Чтобы пользоваться всеми преимуществами <xref:System.Uri> класса, при перегрузке строки следует вызывать <xref:System.Uri> перегрузки, используя строковый аргумент.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Повторно реализовать метод, который используется строковое представление URI, поэтому он создает экземпляр класса <xref:System.Uri> класса, используя строковый аргумент, а затем передает <xref:System.Uri> объект перегрузку, которая имеет <xref:System.Uri> параметра.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если параметр строки не представляет URI.

## <a name="example"></a>Пример
 В следующем примере показано правильно реализованный перегружающий.

 [!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA2234: Передавайте объекты System.Uri вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: Свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI возвращать значения не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)