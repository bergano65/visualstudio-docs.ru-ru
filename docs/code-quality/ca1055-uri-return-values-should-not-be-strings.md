---
title: "CA1055: возвращаемые значения URI не должны быть строками | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1055"
  - "UriReturnValuesShouldNotBeStrings"
helpviewer_keywords: 
  - "CA1055"
  - "UriReturnValuesShouldNotBeStrings"
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA1055: возвращаемые значения URI не должны быть строками
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriReturnValuesShouldNotBeStrings|  
|CheckId|CA1055|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 В имени метода содержится "uri", "Uri", "urn", "Urn", "url" или "Url" и метод возвращает строку.  
  
## Описание правила  
 Данное правило разбивает имя метода на маркеры на основе соглашения о регистре Pascal и проверяет равенство каждого маркера "uri", "Uri", "urn", "Urn", "url" или "Url".  В случае совпадения правило допускает, что метод возвращает универсальный код ресурса \(URI\).  В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности.  Класс <xref:System.Uri?displayProperty=fullName> предоставляет аналогичные службы более надежным и безопасным способом.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, измените возвращаемый тип на <xref:System.Uri>.  
  
## Отключение предупреждений  
 Отключить предупреждение из этого правила можно без последствий, если возвращаемое значение не представляет URI.  
  
## Пример  
 В следующем примере показан тип `ErrorProne`, нарушающий это правило, и тип `SaferWay`, соответствующий этому правилу.  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]  
  
## Связанные правила  
 [CA1056: свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA2234: передавайте объекты System.Uri вместо строк](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1057: перегрузки строковых параметров URI вызывают перегрузки System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)