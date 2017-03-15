---
title: "CA1303: не следует передавать литералы в виде локализованных параметров | Microsoft Docs"
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
  - "Do not pass literals as localized parameters"
  - "DoNotPassLiteralsAsLocalizedParameters"
  - "CA1303"
helpviewer_keywords: 
  - "CA1303"
  - "DoNotPassLiteralsAsLocalizedParameters"
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1303: не следует передавать литералы в виде локализованных параметров
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Метод передает строковый литерал в виде параметра конструктору или методу в библиотеке классов [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], и эта строка должна быть локализуемой.  
  
 Это предупреждение выдается, если строковый литерал передается как значение параметру или свойству и выполняется одно или несколько из следующих условий:  
  
-   Значение атрибута <xref:System.ComponentModel.LocalizableAttribute> параметра или свойства равно "true".  
  
-   Имя параметра или свойства содержит "Text", "Message" или "Caption".  
  
-   Имя строкового параметра, который передается методу Console.Write или Console.WriteLine, равно "value" или "format".  
  
## Описание правила  
 Сложно локализовать строковые литералы, внедренные в исходный код.  
  
## Устранение нарушений  
 Чтобы исправить нарушение этого правила, необходимо заменить строковый литерал строкой, извлекаемой с помощью экземпляра класса <xref:System.Resources.ResourceManager>.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении данного правила безопасно в том случае, если библиотека кода не предназначена для локализации, либо строка не предоставляется пользователю, либо разработчик использует библиотеку кода.  
  
 Пользователи могут избавиться от помех методам, которым не должны передаваться локализованные строки, либо переименовав параметр или свойство с именем, либо пометив эти элементы как условные.  
  
## Пример  
 В следующем примере показан метод, который создает исключение, если любой из его двух аргументов оказывается за пределами допустимого диапазона.  Для первого аргумента конструктору исключения передается строковый литерал, что нарушает данное правило.  Для второго аргумента конструктору правильно передается строка, извлеченная с помощью <xref:System.Resources.ResourceManager>.  
  
 [!CODE [FxCop.Globalization.DoNotPassLiterals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals#1)]  
  
## См. также  
 [Ресурсы в приложениях для настольных систем](../Topic/Resources%20in%20Desktop%20Apps.md)