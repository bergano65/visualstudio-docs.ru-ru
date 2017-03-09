---
title: "Отсутствует доступный метод &quot;&lt;procedurename&gt;&quot; с сигнатурой, совместимой с делегатом &quot;&lt;delegatename&gt;&quot;:&lt;suberrorlist&gt; | Microsoft Docs"
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
  - "bc30950"
  - "vbc30950"
helpviewer_keywords: 
  - "BC30950"
ms.assetid: c1938099-2c03-491e-b599-d0c43bf94baf
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Отсутствует доступный метод &quot;&lt;procedurename&gt;&quot; с сигнатурой, совместимой с делегатом &quot;&lt;delegatename&gt;&quot;:&lt;suberrorlist&gt;
Оператор присваивания назначает адрес процедуры переменной делегата, но компилятор не может найти версию процедуры с соответствующей сигнатурой.  
  
 Когда код использует адрес процедуры, компилятор пытается найти версию этой процедуры со списком параметров, который соответствует списку делегата. Если процедура определена в нескольких перегруженных версиях, компилятор пытается найти одну версию с соответствующей сигнатурой. Для получения дополнительной информации см. [Разрешение перегрузки](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution).  
  
 Если компилятор не может найти какую\-либо версию процедуры с соответствующей сигнатурой, он выдает эту ошибку. Это может произойти, например, если процедура или делегат является универсальным объектом, и в этот объект передается аргумент типа, предоставляющий сигнатуру, которая не соответствует другой сигнатуре.  
  
 **Идентификатор ошибки:** BC30950  
  
### Исправление ошибки  
  
1.  Переопределите процедуру или делегат так, чтобы они имели соответствующие списки параметров.  
  
     \-или\-  
  
     Определите новый делегат со списком параметров, соответствующим списку параметров процедуры, или определите новую процедуру со списком параметров, соответствующим списку делегата.  
  
2.  Если либо процедура, либо делегат является универсальным объектом, то передайте в этот объект аргумент типа, который обеспечит соответствие его сигнатуры другой сигнатуре.  
  
## См. также  
 [Оператор AddressOf](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Оператор Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [НЕ В СБОРКЕ. Делегаты и оператор AddressOf](http://msdn.microsoft.com/ru-ru/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Разрешение перегрузки](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)