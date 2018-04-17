---
title: 'CA1054: Параметры URI не должны быть строками | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6758701dabb0d682dc40fe0fbd8c996adaf0a3c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: параметры URI не должны быть строками
|||  
|-|-|  
|TypeName|UriParametersShouldNotBeStrings|  
|CheckId|CA1054|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Тип объявляет метод с параметром строки, имя которого содержит «uri», «Uri», «urn», «Urn», «url» или «Url» и тип не объявляет соответствующую перегрузку, которая принимает <xref:System.Uri?displayProperty=fullName> параметра.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило разбивает имя параметра на лексемы, основанное на соглашении о верблюжий и проверяет равенство каждого маркера «uri», «Uri», «urn», «Urn», «url» или «Url». В случае совпадения правило считает, что параметр представляет универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. Если метод принимает строковое представление кода URI, соответствующую перегрузку необходимо предоставить, принимающую экземпляр <xref:System.Uri> класс, который предоставляет эти услуги надежным и безопасным способом.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените параметр для <xref:System.Uri> типа; это критическое изменение. Также можно предоставить перегрузку метода, принимающую <xref:System.Uri> параметр; это некритическое изменение.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила, если параметр не представляет универсальный код Ресурса.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип `ErrorProne`, который нарушает это правило и тип, `SaferWay`, соответствующий этому правилу.  
  
 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1056: свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1055: возвращаемые значения URI не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: передавайте объекты System.Uri вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057: перегрузки строковых параметров URI вызывают перегрузки System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)