---
title: "CA1819: свойства не должны возвращать массивы | Microsoft Docs"
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
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
helpviewer_keywords: 
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1819: свойства не должны возвращать массивы
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertiesShouldNotReturnArrays|  
|CheckId|CA1819|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытое или защищенное свойство в открытом типе возвращает массив.  
  
## Описание правила  
 Массивы, возвращаемые свойствами, не защищены от записи, даже если свойство доступно только для чтения.  Чтобы защитить массив от изменений, свойство должно возвращать копию массива.  Как правило, пользователи не понимают требований к производительности при вызове такого свойства.  В частности, они могут использовать это свойство как индексированное.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, либо сделайте свойство методом, либо измените свойство, чтобы оно возвращало коллекцию.  
  
## Отключение предупреждений  
 Атрибуты могут содержать свойства, возвращающие массивы, но не могут содержать свойства, которые возвращают коллекции.  Можно отключить предупреждение, вызываемое для свойства атрибута, производного от класса [System.Attribute](assetId:///System.Attribute?qualifyHint=False&autoUpgrade=True).  В противном случае для этого правила отключать вывод предупреждений не следует.  
  
## Пример нарушения  
  
### Описание  
 В следующем примере показано свойство, нарушающее это правило.  
  
### Код  
 [!code-cs[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]  
  
### Комментарии  
 Чтобы устранить нарушение этого правила, либо сделайте свойство методом, либо измените свойство, чтобы оно возвращало коллекцию вместо массива.  
  
## Пример замены свойства на метод  
  
### Описание  
 В следующем примере это нарушение устраняется путем замены свойства на метод.  
  
### Код  
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-cs[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]  
  
## Пример возврата коллекции  
  
### Описание  
 В следующем примере это нарушение устраняется путем изменения свойства для возврата  
  
 <xref:System.Collection.ObjectModel.ReadOnlyCollection?displayProperty=fullName>.  
  
### Код  
 [!code-cs[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]  
  
## Разрешение пользователям изменять свойство  
  
### Описание  
 Может потребоваться предоставить потребителю класса возможность изменять свойство.  В следующем примере показано свойство, доступное для чтения и записи и нарушающее это правило.  
  
### Код  
 [!code-cs[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]  
  
### Комментарии  
 В следующем примере это нарушение устраняется путем изменения свойства для возврата <xref:System.Collection.ObjectModel.Collection?displayProperty=fullName>.  
  
### Код  
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-cs[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]  
  
## Связанные правила  
 [CA1024: используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)