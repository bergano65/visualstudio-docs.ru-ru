---
title: "CA1309: используйте порядковый параметр StringComparison | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseOrdinalStringComparison"
  - "CA1309"
helpviewer_keywords: 
  - "UseOrdinalStringComparison"
  - "CA1309"
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1309: используйте порядковый параметр StringComparison
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseOrdinalStringComparison|  
|CheckId|CA1309|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Операция сравнения строк, не являющаяся лингвистической, не задает параметру <xref:System.StringComparison> ни значение **Ordinal**, ни **OrdinalIgnoreCase**.  
  
## Описание правила  
 Многие строковые операции, большинство важных методов <xref:System.String.Compare%2A?displayProperty=fullName> и <xref:System.String.Equals%2A?displayProperty=fullName> теперь предоставляют перегрузку, принимающую перечисление <xref:System.StringComparision?displayProperty=fullName> в качестве параметра.  
  
 Если указывается либо **StringComparison.Ordinal**, либо **StringComparison.OrdinalIgnoreCase**, сравнение строк будет нелингвистическим.  То есть при принятии решений на основании сравнения игнорируются функции, характерные для естественного языка.  Это означает, что решения основываются на простых байтовых сравнениях и игнорируют использование таблиц регистров и равенства, параметризованных по языку и региональным параметрам.  В результате за счет явного задания параметру значения **StringComparison.Ordinal** или **StringComparison.OrdinalIgnoreCase** код часто становится более надежным и правильным, кроме того, увеличивается скорость его выполнения.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените метод сравнения строк на перегрузку, принимающую перечисление <xref:System.StringComparison?displayProperty=fullName> в качестве параметра и задайте значение **Ordinal** или **OrdinalIgnoreCase**.  Например, измените `String.Compare(str1, str2)` на `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## Отключение предупреждений  
 Если библиотека или приложение предназначены для ограниченной локальной аудитории или необходимо использовать семантику текущего языка и региональных параметров, для данного правила можно отключить вывод предупреждений.  
  
## См. также  
 [Предупреждения глобализации](../code-quality/globalization-warnings.md)   
 [CA1307: укажите StringComparison](../code-quality/ca1307-specify-stringcomparison.md)