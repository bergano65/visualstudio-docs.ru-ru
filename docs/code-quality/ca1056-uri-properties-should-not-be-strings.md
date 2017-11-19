---
title: "CA1056: Свойства URI не должны быть строками | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 506421ab93cb54c11e1fdfb02c948e4cc8b23d2e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056: свойства URI не должны быть строками
|||  
|-|-|  
|TypeName|UriPropertiesShouldNotBeStrings|  
|CheckId|CA1056|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Тип объявляет строковое свойство, имя которого содержит «uri», «Uri», «urn», «Urn», «url» или «Url».  
  
## <a name="rule-description"></a>Описание правила  
 Это правило разбивает имя свойства на токены, используя соглашения о регистре Pascal и проверяет равенство каждого маркера «uri», «Uri», «urn», «Urn», «url» или «Url». В случае совпадения правило предполагает, что свойство представляет универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. <xref:System.Uri?displayProperty=fullName> Класс предоставляет эти услуги надежным и безопасным способом.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените свойства на <xref:System.Uri> типа.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, если свойство не представляет универсальный код Ресурса.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип `ErrorProne`, который нарушает это правило и тип, `SaferWay`, соответствующий этому правилу.  
  
 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1054: параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: возвращаемые значения URI не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: передавайте объекты System.Uri вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057: перегрузки строковых параметров URI вызывают перегрузки System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)