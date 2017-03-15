---
title: "Метод &quot;&lt;имя_метода1&gt;&quot; не имеет такие же универсальные ограничения, как разделяемый метод &quot;&lt;имя_метода2&gt;&quot; | Microsoft Docs"
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
  - "bc31438"
  - "vbc31438"
helpviewer_keywords: 
  - "BC31438"
ms.assetid: ea092f0c-661b-49db-80c1-76401fc8bc0b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод &quot;&lt;имя_метода1&gt;&quot; не имеет такие же универсальные ограничения, как разделяемый метод &quot;&lt;имя_метода2&gt;&quot;
Вы определили реализацию разделяемого метода, имеющую универсальные ограничения, которые отличаются от ограничений в объявлении разделяемого метода. Это проиллюстрировано в следующем коде.  
  
```vb#  
Partial Class Class1 Partial Private Sub Test(Of T As Class)(ByVal arg As T) End Sub End Class Partial Class Class1 '' The error occurs here, for Test. 'Private Sub Test(Of T As Structure)(ByVal arg As T) 'End Sub End Class  
```  
  
 **Error ID:** BC31438  
  
## См. также  
 [Разделяемые методы](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)