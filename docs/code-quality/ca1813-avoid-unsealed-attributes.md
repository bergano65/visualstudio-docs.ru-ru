---
title: "CA1813: не допускайте использования распечатанных атрибутов | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1813"
  - "AvoidUnsealedAttributes"
helpviewer_keywords: 
  - "AvoidUnsealedAttributes"
  - "CA1813"
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1813: не допускайте использования распечатанных атрибутов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnsealedAttributes|  
|CheckId|CA1813|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытый тип, наследующий от класса <xref:System.Attribute?displayProperty=fullName>, не является абстрактным и запечатанным \(`NotInheritable` в Visual Basic\).  
  
## Описание правила  
 В библиотеке классов [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] предоставляются методы для извлечения пользовательских атрибутов.  По умолчанию, эти методы выполняют поиск в иерархии наследования атрибутов; например, метод <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> выполняет поиск указанного типа атрибута или всех типов атрибутов, которые расширяют указанный тип.  Если запечатать атрибут, поиск в иерархии наследования выполняться не будет, в результате чего может повыситься производительность.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, запечатайте атрибут или сделайте его абстрактным.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении этого правила является безопасным.  Предупреждения следует отключать в том случае, если определяется иерархия атрибутов, но запечатывание атрибута или его изменение с помощью модификатора "abstract" не представляется возможным.  
  
## Пример  
 В следующем примере показан пользовательский атрибут, который соответствует данному правилу.  
  
 [!code-cs[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## Связанные правила  
 [CA1019: необходимо определять методы доступа для аргументов атрибутов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018: помечайте атрибуты как AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## См. также  
 [Атрибуты](../Topic/Attributes1.md)