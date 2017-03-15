---
title: "Отсутствует доступная процедура &quot;&lt;имя процедуры&gt;&quot;, которая является наиболее подходящей: &lt;список_сигнатур&gt;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30794"
  - "BC30794"
helpviewer_keywords: 
  - "BC30794"
ms.assetid: 51d54cbb-b530-4661-9952-5ccc17e4220b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Отсутствует доступная процедура &quot;&lt;имя процедуры&gt;&quot;, которая является наиболее подходящей: &lt;список_сигнатур&gt;.
Оператор присваивания назначает адрес перегруженной процедуры переменной делегата, но компилятор не может выбрать одну из перегруженных версий.  
  
 Когда код использует адрес процедуры, которая определена в нескольких перегруженных версиях, компилятор должен решить, какую из перегрузок следует использовать. Он пытается найти единственную версию со списком параметров, который соответствует списку параметров делегатов. Дополнительные сведения см. в разделе [Разрешение перегрузки](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution).  
  
 Если компилятор находит несколько версий процедуры с соответствующей сигнатурой, он выдает эту ошибку. Это может произойти, например, если одна из перегрузок является универсальной, и передаваемый в нее аргумент типа делает ее сигнатуру идентичной сигнатуре другой перегрузки.  
  
 **Идентификатор ошибки:** BC30794  
  
### Исправление ошибки  
  
-   Если конфликт вызван универсальной перегрузкой с такой же сигнатурой, что и другая перегрузка, измените аргумент типа, передаваемый в эту универсальную перегрузку.  
  
## См. также  
 [Оператор AddressOf](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Оператор Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [НЕ В СБОРКЕ. Делегаты и оператор AddressOf](http://msdn.microsoft.com/ru-ru/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Разрешение перегрузки](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)