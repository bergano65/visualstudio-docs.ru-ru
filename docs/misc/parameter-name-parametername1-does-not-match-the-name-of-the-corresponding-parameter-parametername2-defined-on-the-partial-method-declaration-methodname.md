---
title: "Имя параметра &quot;&lt;имя_параметра1&gt;&quot; не отвечает имени соответствующего параметра &quot;&lt;имя_параметра2&gt;&quot;, определенного в объявлении разделяемого метода &quot;&lt;имя_метода&gt;&quot; | Microsoft Docs"
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
  - "vbc31442"
  - "bc31442"
helpviewer_keywords: 
  - "BC31442"
ms.assetid: 7f097bb2-071a-42ec-b7af-40da04f602f2
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Имя параметра &quot;&lt;имя_параметра1&gt;&quot; не отвечает имени соответствующего параметра &quot;&lt;имя_параметра2&gt;&quot;, определенного в объявлении разделяемого метода &quot;&lt;имя_метода&gt;&quot;
Когда предоставляются параметры в объявлении и реализации разделяемого метода, имена соответствующих параметров должны совпадать. Например, приведенный ниже код вызывает эту ошибку.  
  
```vb#  
Partial Class Product  
  
    ' Declaration of the partial method.  
    Partial Private Sub valueChanged(ByVal newVal As Integer)  
    End Sub  
End Class  
```  
  
```vb#  
Partial Class Product  
  
    ' Implementation of the partial method. This error is  
    ' reported for parameter val.  
    ' Private Sub valueChanged(ByVal val As Integer)  
    '     MsgBox(Value was changed to " & Me.Quantity)  
    ' End Sub  
  
End Class  
```  
  
 **Идентификатор ошибки:** BC31442  
  
### Исправление ошибки  
  
1.  Измените имя параметра или имена параметров в объявлении или реализации так, чтобы соответствующие параметры имели одинаковые имена.  
  
## См. также  
 [Разделяемые методы](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)