---
title: "CA1820: проверьте наличие пустых строк путем проверки длины строки | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
helpviewer_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1820: проверьте наличие пустых строк путем проверки длины строки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TestForEmptyStringsUsingStringLength|  
|CheckId|CA1820|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Строка сравнивается с пустой строкой с помощью метода <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## Описание правила  
 Сравнение строк с помощью свойства <xref:System.String.Length%2A?displayProperty=fullName> или метода <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> выполняется значительно быстрее, чем сравнение с помощью метода <xref:System.Object.Equals%2A>.  Это происходит потому, что метод <xref:System.Object.Equals%2A> выполняет значительно больше инструкций MSIL, чем метод <xref:System.String.IsNullOrEmpty%2A>. Число инструкций MSIL также превышает количество инструкций, необходимых для извлечения значения свойства <xref:System.String.Length%2A> и сравнения этого значения с нулем.  
  
 Следует принять во внимание, что метод <xref:System.Object.Equals%2A> и выражение <xref:System.String.Length%2A> \=\= 0 ведут себя по\-разному в случае неопределенных строк.  При попытке получить значение свойства <xref:System.String.Length%2A> для неопределенной строки среда CLR создает исключение <xref:System.NullReferenceException?displayProperty=fullName>.  При выполнении сравнения неопределенной строки с пустой строкой среда CLR не создает исключение, а сравнение возвращает значение `false`.  Проверка на наличие значения NULL не оказывает существенного влияния на относительную производительность этих двух подходов.  При разработке кода для среды [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] используйте метод <xref:System.String.IsNullOrEmpty%2A>.  Во всех остальных случаях рекомендуется по возможности использовать сравнение <xref:System.String.Length%2A> \=\=.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, замените метод сравнения на использование свойства <xref:System.String.Length%2A> и выполните проверку на равенство с неопределенной строкой.  При разработке кода для среды [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] используйте метод <xref:System.String.IsNullOrEmpty%2A>.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении этого правила является безопасным в том случае, если вопросы производительности не являются основным приоритетом.  
  
## Пример  
 В следующем примере демонстрируются различные способы поиска пустой строки.  
  
 [!CODE [FxCop.Performance.StringTest#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest#1)]