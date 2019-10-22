---
title: 'CA1057: перегрузки строковых URI вызывают перегрузки System. URI | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba7e7de4f3ef6336ed3d82dc1e1da03ec0bf2575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603074"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: перегрузки строковых параметров URI вызывают перегрузки System.Uri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип объявляет перегрузки метода, которые отличаются только заменой строкового параметра параметром <xref:System.Uri?displayProperty=fullName>, а перегрузка, принимающая строковый параметр, не вызывает перегрузку, которая принимает параметр <xref:System.Uri>.

## <a name="rule-description"></a>Описание правила
 Поскольку перегрузки отличаются только параметром String/<xref:System.Uri>, предполагается, что строка представляет универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. Класс <xref:System.Uri> предоставляет эти службы безопасным и безопасным способом. Чтобы воспользоваться преимуществами класса <xref:System.Uri>, строка перегрузки должна вызывать перегрузку <xref:System.Uri> с помощью строкового аргумента.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Повторно реализуйте метод, который использует строковое представление универсального кода ресурса (URI), чтобы создать экземпляр класса <xref:System.Uri> с помощью строкового аргумента, а затем передает объект <xref:System.Uri> в перегрузку, имеющую параметр <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если строковый параметр не представляет URI.

## <a name="example"></a>Пример
 В следующем примере показана правильно реализованная перегрузка строки.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2234: передавайте объекты System.Uri вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: возвращаемые значения URI не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
