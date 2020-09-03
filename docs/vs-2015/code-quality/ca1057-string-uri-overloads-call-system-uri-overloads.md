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
ms.openlocfilehash: bcdb4d8333b0a4d2d06580d882cf736d4527eca4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539533"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057. Перегрузки строковых параметров URI вызывают перегрузки System.Uri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип объявляет перегрузки метода, которые отличаются только заменой строкового параметра <xref:System.Uri?displayProperty=fullName> параметром, а перегрузка, принимающая строковый параметр, не вызывает перегрузку, которая принимает <xref:System.Uri> параметр.

## <a name="rule-description"></a>Описание правила
 Поскольку перегрузки отличаются только строкой или <xref:System.Uri> параметром, предполагается, что строка представляет универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. <xref:System.Uri>Класс предоставляет эти службы безопасным и безопасным способом. Чтобы воспользоваться преимуществами <xref:System.Uri> класса, перегрузка строки должна вызывать <xref:System.Uri> перегрузку с помощью строкового аргумента.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Повторно реализуйте метод, который использует строковое представление универсального кода ресурса (URI), чтобы создать экземпляр <xref:System.Uri> класса с помощью строкового аргумента, а затем передает <xref:System.Uri> объект в перегрузку, имеющую <xref:System.Uri> параметр.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если строковый параметр не представляет URI.

## <a name="example"></a>Пример
 В следующем примере показана правильно реализованная перегрузка строки.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2234. Передавайте объекты System.Uri вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056. Свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054. Параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055. Возвращаемые значения URI не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
