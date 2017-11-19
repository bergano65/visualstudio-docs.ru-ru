---
title: "CA1055: Возвращаемые URI значения не должны быть строками | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 99ada3927275541e3b129c79bbcaac66f0aa5bdd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055: возвращаемые значения URI не должны быть строками
|||  
|-|-|  
|TypeName|UriReturnValuesShouldNotBeStrings|  
|CheckId|CA1055|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Имя метода содержит «uri», «Uri», «urn», «Urn», «url» или «Url», а метод возвращает строку.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило разбивает имя метода на маркеры на основании соглашения о регистре Pascal и проверяет равенство каждого маркера «uri», «Uri», «urn», «Urn», «url» или «Url». В случае совпадения правиле предполагается, что метод возвращает универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. <xref:System.Uri?displayProperty=fullName> Класс предоставляет эти услуги надежным и безопасным способом.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените тип возвращаемого значения для <xref:System.Uri>.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, если возвращаемое значение не представляет универсальный код Ресурса.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип `ErrorProne`, который нарушает это правило и тип, `SaferWay`, соответствующий этому правилу.  
  
 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1056: свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA2234: передавайте объекты System.Uri вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057: перегрузки строковых параметров URI вызывают перегрузки System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)