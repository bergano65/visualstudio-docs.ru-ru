---
title: "CA1018: помечайте атрибуты как AttributeUsageAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
helpviewer_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1018: помечайте атрибуты как AttributeUsageAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAttributesWithAttributeUsage|  
|CheckId|CA1018|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Атрибут <xref:System.AttributeUsageAttribute?displayProperty=fullName> отсутствует у настраиваемого атрибута.  
  
## Описание правила  
 При определении настраиваемого атрибута его нужно пометить с помощью <xref:System.AttributeUsageAttribute>, чтобы указать, где в исходном коде можно применить настраиваемый атрибут.  Допустимое положение атрибута в коде зависит от значения атрибута и его применения.  Например можно определить атрибут, который позволяет определить лицо, ответственное за поддержку и улучшение каждого типа в библиотеке; ответственность всегда назначается на уровне типа.  В этом случае компиляторы должны включать атрибут на классы, перечисления и интерфейсы, но не нужно включать его методы, события или свойства.  Возможность применения атрибута к сборкам зависит от организационных политик и процедур.  
  
 Перечисление <xref:System.AttributeTargets?displayProperty=fullName> определяет целевые объекты для пользовательского атрибута.  Если опустить <xref:System.AttributeUsageAttribute>, то пользовательский атрибут будет доступен для всех целевых объектов согласно значению `All` перечисления <xref:System.AttributeTargets>.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, укажите целевые объекты для атрибута с помощью <xref:System.AttributeUsageAttribute>.  См. следующий пример.  
  
## Отключение предупреждений  
 Вместо отключения предупреждений следует устранить нарушение этого правила.  Даже если атрибут наследует <xref:System.AttributeUsageAttribute>, атрибут должен присутствовать, поскольку в этом случае упрощается обслуживание кода.  
  
## Пример  
 В следующем примере определяются два атрибута.  `BadCodeMaintainerAttribute` неправильно опускает инструкцию <xref:System.AttributeUsageAttribute>, и `GoodCodeMaintainerAttribute` правильно реализует атрибут, который описан ранее в этом разделе.  Обратите внимание, что свойство `DeveloperName` необходимо по правилу проектирования [CA1019: необходимо определять методы доступа для аргументов атрибутов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) и включено для полноты.  
  
 [!code-cs[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## Связанные правила  
 [CA1019: необходимо определять методы доступа для аргументов атрибутов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813: не допускайте использования распечатанных атрибутов](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## См. также  
 [Атрибуты](../Topic/Attributes1.md)