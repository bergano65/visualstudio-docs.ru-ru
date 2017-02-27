---
title: "CA1307: укажите StringComparison | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1307"
  - "SpecifyStringComparison"
helpviewer_keywords: 
  - "CA1307"
  - "SpecifyStringComparison"
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1307: укажите StringComparison
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|CheckId|CA1307|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## Причина  
 В операции сравнения строк используется перегрузка метода, которая не устанавливает параметр <xref:System.StringComparison>.  
  
## Описание правила  
 Многие операции со строками \(в первую очередь методы <xref:System.String.Compare%2A> и <xref:System.String.Equals%2A>\) предоставляют перегрузки, которые принимают в качестве параметра перечисление <xref:System.StringComparison>.  
  
 Если существует перегрузка, которая принимает параметр <xref:System.StringComparison>, следует использовать ее, а не другую перегрузку, не принимающую этого параметра.  При явном задании этого параметра код зачастую становится более ясным и простым для использования.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, замените методы сравнения строк на перегрузки, которые принимают в качестве параметра перечисление <xref:System.StringComparison>.  Например, замените `String.Compare(str1, str2)` на метод `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении данного правила безопасно в том случае, если библиотека или приложение предназначено для ограниченного использования в одном регионе и поэтому их локализация не планируется.  
  
## См. также  
 [Предупреждения глобализации](../code-quality/globalization-warnings.md)   
 [CA1309: используйте порядковый параметр StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)