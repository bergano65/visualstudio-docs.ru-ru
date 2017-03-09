---
title: "Имя параметра типа &quot;&lt;имя_параметра_типа1&gt;&quot; не отвечает имени соответствующего параметра типа &quot;&lt;имя_параметра_типа2&gt;&quot;, определенного в объявлении разделяемого метода &quot;&lt;имя_метода&gt;&quot;. | Microsoft Docs"
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
  - "vbc31443"
  - "bc31443"
helpviewer_keywords: 
  - "BC31443"
ms.assetid: 27c81cc1-325e-4e86-9d00-34f81e928076
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Имя параметра типа &quot;&lt;имя_параметра_типа1&gt;&quot; не отвечает имени соответствующего параметра типа &quot;&lt;имя_параметра_типа2&gt;&quot;, определенного в объявлении разделяемого метода &quot;&lt;имя_метода&gt;&quot;.
В разделяемом методе, который включает один или несколько параметров типа, имена параметров типа должны быть одинаковыми в объявлении метода и в реализации метода.  
  
 Например, следующие объявление и реализация вызывают эту ошибку.  
  
```vb#  
' Definition of the partial method signature with type parameter T. Partial Private Sub OnNameChanged(Of T)() End Sub  
```  
  
```vb#  
'' Implementation of the partial method with type parameter N. 'Private Sub OnNameChanged(Of N)() '    Console.WriteLine("Name was changed to " & Me.Name) 'End Sub  
```  
  
 **Идентификатор ошибки:** BC31443  
  
### Исправление ошибки  
  
-   Проверьте параметры типа, чтобы определить, где они не совпадают. Где это необходимо, измените имена, чтобы сделать их одинаковыми.  
  
## См. также  
 [Разделяемые методы](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)