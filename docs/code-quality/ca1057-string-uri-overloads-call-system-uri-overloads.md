---
title: "CA1057: перегрузки строковых параметров URI вызывают перегрузки System.Uri | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1057"
  - "StringUriOverloadsCallSystemUriOverloads"
helpviewer_keywords: 
  - "StringUriOverloadsCallSystemUriOverloads"
  - "CA1057"
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1057: перегрузки строковых параметров URI вызывают перегрузки System.Uri
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StringUriOverloadsCallSystemUriOverloads|  
|CheckId|CA1057|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## Причина  
 В типе объявляются перегрузки метода, которые отличаются лишь тем, что в одной используется строковый параметр, а в другой — параметр <xref:System.Uri?displayProperty=fullName>. Однако перегрузка, принимающая строковый параметр, не вызывает перегрузку, принимающую параметр <xref:System.Uri>.  
  
## Описание правила  
 Поскольку перегрузки отличаются только использованием строкового параметра или параметра <xref:System.Uri>, то предполагается, что строка представляет универсальный код ресурса \(URI\).  В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности.  Класс <xref:System.Uri> предоставляет аналогичные службы более надежным и безопасным способом.  Чтобы воспользоваться преимуществами класса <xref:System.Uri>, перегрузка, принимающая строковый параметр, должна вызывать перегрузку <xref:System.Uri>, используя строковый аргумент.  
  
## Устранение нарушений  
 Повторно реализуйте метод, использующий строковое представление кода URI, таким образом, чтобы он создавал экземпляр класса <xref:System.Uri>, используя строковый аргумент, а затем передавал объект <xref:System.Uri> в перегрузку, которая принимает параметр <xref:System.Uri>.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении данного правила безопасно в том случае, если строковый параметр не представляет код URI.  
  
## Пример  
 В следующем примере показана правильно реализованная строковая перегрузка.  
  
 [!CODE [FxCop.Design.CallUriOverload#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload#1)]  
  
## Связанные правила  
 [CA2234: передавайте объекты System.Uri вместо строк](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1056: свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: возвращаемые значения URI не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)