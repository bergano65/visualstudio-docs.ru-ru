---
title: "CA2243: синтаксический анализ строковых литералов атрибута должен осуществляться правильно | Microsoft Docs"
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
  - "CA2243"
  - "AttributeStringLiteralsShouldParseCorrectly"
helpviewer_keywords: 
  - "AttributeStringLiteralsShouldParseCorrectly"
  - "CA2243"
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2243: синтаксический анализ строковых литералов атрибута должен осуществляться правильно
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AttributeStringLiteralsShouldParseCorrectly|  
|CheckId|CA2243|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Не удается правильно выполнить синтаксический анализ строкового литерала атрибута, представляющего URL\-адрес, идентификатор GUID или версию.  
  
## Описание правила  
 Поскольку атрибуты наследуют от атрибута <xref:System.Attribute?displayProperty=fullName> и используются во время компиляции, конструкторам можно передавать только константные значения.  Параметры атрибутов, которые должны представлять URL\-адреса, идентификаторы GUID или версии, не могут принадлежать типам <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName> и <xref:System.Version?displayProperty=fullName>, поскольку эти типы не могут представляться константами.  Эти параметры должны представляться строками.  
  
 Поскольку параметр принадлежит строковому типу, во время компиляции может быть передан параметр неправильного формата.  
  
 Данное правило с помощью эвристики именования выполняет поиск параметров, которые представляют универсальный код ресурса \(URI\), глобальный уникальный идентификатор \(GUID\) или версию, и проверяют правильность передаваемого значения.  
  
## Устранение нарушений  
 Замените строку параметра на URL\-адрес, идентификатор GUID или версию правильного формата.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении данного правила безопасно в том случае, если параметр не представляет URL\-адрес, идентификатор GUID или версию.  
  
## Пример  
 В следующем примере показан код для атрибута AssemblyFileVersionAttribute, который нарушает данное правило.  
  
 [!code-cs[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]  
  
 Нарушение правила вызывается параметрами, которые  
  
-   содержат ключевое слово "version", однако не могут быть синтаксически разобраны в соответствии с типом System.Version;  
  
-   содержат ключевое слово "guid", однако не могут быть синтаксически разобраны в соответствии с типом System.Guid;  
  
-   содержат ключевые слова "uri", "urn" или "url", однако не могут быть синтаксически разобраны в соответствии с типом System.Uri.  
  
## См. также  
 [CA1054: параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)