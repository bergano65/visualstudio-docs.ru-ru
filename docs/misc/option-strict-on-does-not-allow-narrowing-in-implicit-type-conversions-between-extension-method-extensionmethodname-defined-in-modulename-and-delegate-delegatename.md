---
title: "&quot;Option Strict On&quot; не разрешает сужение в неявных преобразованиях типа между методом расширения &quot;&lt;имя_метода_расширения&gt;&quot;, заданном в модуле &quot;&lt;имя_модуля&gt;&quot;, и делегатом &quot;&lt;имя_делегата&gt;&quot;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36709"
  - "vbc36709"
helpviewer_keywords: 
  - "BC36709"
ms.assetid: 95d8c833-3525-411b-98e8-b7d3f61f75c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Option Strict On&quot; не разрешает сужение в неявных преобразованиях типа между методом расширения &quot;&lt;имя_метода_расширения&gt;&quot;, заданном в модуле &quot;&lt;имя_модуля&gt;&quot;, и делегатом &quot;&lt;имя_делегата&gt;&quot;.
С "`Option Strict` on" у вас не может быть сужающего преобразования от типа данных параметра в делегате до соответствующего параметра метода расширения, назначенного переменной этого типа делегата. Тип данных параметра делегата должен расширяться к типу данных метода расширения.  
  
 **Идентификатор ошибки:** BC36709  
  
### Исправление ошибки  
  
-   Измените тип данных параметра в делегате или методе расширения, чтобы существовало необходимое расширяющее отношение.  
  
## См. также  
 [Методы расширения](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Неявное преобразование делегата](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Делегаты](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Расширяющие и сужающие преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [НЕ В СБОРКЕ. Делегаты и оператор AddressOf](http://msdn.microsoft.com/ru-ru/7b2ed932-8598-4355-b2f7-5cedb23ee86f)