---
title: "CA1056: свойства URI не должны быть строками | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UriPropertiesShouldNotBeStrings"
  - "CA1056"
helpviewer_keywords: 
  - "CA1056"
  - "UriPropertiesShouldNotBeStrings"
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA1056: свойства URI не должны быть строками
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriPropertiesShouldNotBeStrings|  
|CheckId|CA1056|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Тип объявляет строковое свойство, имя которого содержит подстроку "uri", "Uri", "urn", "Urn", "url" или "Url".  
  
## Описание правила  
 Данное правило разбивает имя свойства на лексемы на основе соглашения об использовании прописных и строчных букв языка Pascal и проверяет каждую лексему на равенство подстроке "uri", "Uri", "urn", "Urn", "url" или "Url".  При обнаружении совпадения правило считает, что данное свойство представляет универсальный код ресурса \(URI\).  В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности.  Класс <xref:System.Uri?displayProperty=fullName> предоставляет аналогичные службы более надежным и безопасным способом.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените свойство на тип <xref:System.Uri>.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении данного правила безопасно в том случае, если свойство не представляет код URI.  
  
## Пример  
 В следующем примере показан тип `ErrorProne`, нарушающий это правило, и тип `SaferWay`, соответствующий этому правилу.  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]  
  
## Связанные правила  
 [CA1054: параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: возвращаемые значения URI не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: передавайте объекты System.Uri вместо строк](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1057: перегрузки строковых параметров URI вызывают перегрузки System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)