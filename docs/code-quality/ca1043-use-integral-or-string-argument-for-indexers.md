---
title: "CA1043: используйте целый или строковый аргумент для индексаторов | Microsoft Docs"
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
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
helpviewer_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1043: используйте целый или строковый аргумент для индексаторов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseIntegralOrStringArgumentForIndexers|  
|CheckId|CA1043|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытый или защищенный тип содержит открытый или защищенный индексатор, использующий тип индекса, отличный от <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName> или <xref:System.String?displayProperty=fullName>.  
  
## Описание правила  
 Индексаторы, то есть индексированные свойства, должны использовать для индекса целочисленные или строковые типы.  Эти типы обычно используются для индексации структур данных и повышения удобства использования библиотеки.  Тип <xref:System.Object> следует использовать только в том случае, если во время разработки невозможно указать определенный целочисленный или строковый тип.  Если в программе требуется использовать другие типы индекса, проверьте еще раз, представляет ли тип логическое хранилище данных.  Если тип не представляет логическое хранилище данных, используйте метод.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, укажите для индекса целочисленный или строковый тип или используйте вместо индексатора метод.  
  
## Отключение предупреждений  
 Предупреждения о нарушении этого правила следует отключать только после тщательной проверки необходимости использовать нестандартный индексатор.  
  
## Пример  
 В следующем примере показан индексатор, который использует индекс типа <xref:System.Int32>.  
  
 [!CODE [FxCop.Design.IntegralOrStringIndexers#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers#1)]  
  
## Связанные правила  
 [CA1023: индексы не должны быть многомерными](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)  
  
 [CA1024: используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)