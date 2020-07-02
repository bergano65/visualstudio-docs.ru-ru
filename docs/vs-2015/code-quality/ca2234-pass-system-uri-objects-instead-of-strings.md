---
title: 'CA2234: Передача объектов System. URI вместо строк | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ce5c076260886def089118a4d7211d75e0185c0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545214"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234. Передавайте объекты System.Uri вместо строк
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Выполняется вызов метода, имеющего строковый параметр, имя которого содержит "URI", "URI", "urn", "urn", "URL" или "URL"; и объявляющий тип метода содержит соответствующую перегрузку метода, имеющую <xref:System.Uri?displayProperty=fullName> параметр.

## <a name="rule-description"></a>Описание правила
 Имя параметра разбивается на маркеры в соответствии с соглашением о регистрах Camel, а затем каждый маркер проверяется на равенство "URI", "URI", "urn", "urn", "URL" или "URL". При совпадении предполагается, что параметр представляет универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. <xref:System.Uri>Класс предоставляет эти службы безопасным и безопасным способом. Если существует выбор между двумя перегрузками, которые отличаются только представлением URI, пользователь должен выбрать перегрузку, которая принимает <xref:System.Uri> аргумент.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите перегрузку, которая принимает <xref:System.Uri> аргумент.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если строковый параметр не представляет URI.

## <a name="example"></a>Пример
 В следующем примере показан метод, `ErrorProne` который нарушает правило и метод, `SaferWay` который правильно вызывает <xref:System.Uri> перегрузку.

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1057. Перегрузки строковых параметров URI вызывают перегрузки System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056. Свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054. Параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055. Возвращаемые значения URI не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
