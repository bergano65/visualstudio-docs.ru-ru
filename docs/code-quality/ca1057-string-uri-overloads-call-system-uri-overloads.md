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
ms.openlocfilehash: 41d3db6e4807c77236868e3ab5746da971ddce6c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922493"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057. Перегрузки строковых параметров URI вызывают перегрузки System.Uri

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип объявляет перегрузки метода, которые отличаются только заменой строкового параметра <xref:System.Uri?displayProperty=fullName> параметром, а перегрузка, принимающая строковый параметр, не вызывает перегрузку, которая <xref:System.Uri> принимает параметр.

## <a name="rule-description"></a>Описание правила
Поскольку перегрузки отличаются только строкой или <xref:System.Uri> параметром, предполагается, что строка представляет универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. <xref:System.Uri> Класс предоставляет эти службы безопасным и безопасным способом. Чтобы воспользоваться преимуществами <xref:System.Uri> класса, перегрузка строки должна <xref:System.Uri> вызывать перегрузку с помощью строкового аргумента.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Повторно реализуйте метод, который использует строковое представление универсального кода ресурса (URI), чтобы создать <xref:System.Uri> экземпляр класса с помощью строкового аргумента, а <xref:System.Uri> затем передает объект в перегрузку <xref:System.Uri> , имеющую параметр.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Можно отключить вывод предупреждения из этого правила, если строковый параметр не представляет URI.

## <a name="example"></a>Пример
В следующем примере показана правильно реализованная перегрузка строки.

[!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
[!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
[!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Связанные правила
[CA2234 Передавать объекты System. URI вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

[CA1056: Свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

[CA1054: Параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

[CA1055: Возвращаемые значения URI не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)