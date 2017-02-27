---
title: "CA1054: параметры URI не должны быть строками | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
helpviewer_keywords: 
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1054: параметры URI не должны быть строками
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriParametersShouldNotBeStrings|  
|CheckId|CA1054|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Тип объявляет метод со строковым параметром, имя которого содержит текст "uri", "Uri", "urn", "Urn", "url" или "Url", а тип не объявляет соответствующую перегрузку, принимающую параметр <xref:System.Uri?displayProperty=fullName>.  
  
## Описание правила  
 Это правило разбивает имя параметра на лексемы в соответствии со стилем Camel и проверяет совпадение каждой лексемы со словами "uri", "Uri", "urn", "Urn", "url" или "Url".  При обнаружении совпадения правило считает, что параметр представляет универсальный код ресурса \(URI\).  В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности.  Если метод принимает строковое представление URI, необходимо предоставить соответствующую перегрузку, принимающую экземпляр класса <xref:System.Uri>, который предоставляет эти услуги безопасным образом.  
  
## Устранение нарушений  
 Чтобы исправить нарушение этого правила, измените тип параметра на <xref:System.Uri>; это критическое изменение.  Также можно предоставить перегрузку метода, принимающую параметр <xref:System.Uri>; это некритическое изменение.  
  
## Отключение предупреждений  
 Можно безопасно отключать предупреждения этого правила, если параметр не представляет URI.  
  
## Пример  
 В следующем примере показан тип `ErrorProne`, нарушающий это правило, и тип `SaferWay`, соответствующий этому правилу.  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]  
  
## Связанные правила  
 [CA1056: свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1055: возвращаемые значения URI не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: передавайте объекты System.Uri вместо строк](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1057: перегрузки строковых параметров URI вызывают перегрузки System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)