---
title: "Метод &quot;&lt;имя_метода1&gt;&quot; должен быть объявлен как &quot;Private&quot; для реализации разделяемого метода &quot;&lt;имя_метода2&gt;&quot;. | Microsoft Docs"
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
  - "vbc31441"
  - "bc31441"
helpviewer_keywords: 
  - "BC31441"
ms.assetid: 4d8d19ad-0c3b-4eba-ada8-2cfa6ae795c4
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод &quot;&lt;имя_метода1&gt;&quot; должен быть объявлен как &quot;Private&quot; для реализации разделяемого метода &quot;&lt;имя_метода2&gt;&quot;.
Реализация разделяемого метода должна быть объявлена как `Private`. Например, следующий код вызывает эту ошибку.  
  
```vb#  
Partial Class Product ' Declaration of the partial method. Partial Private Sub valueChanged() End Sub End Class  
```  
  
```vb#  
Partial Class Product ' Implementation of the partial method, with Private missing, ' causes this error. 'Sub valueChanged() '    MsgBox(Value was changed to " & Me.Quantity) 'End Sub End Class  
```  
  
 **Идентификатор ошибки:** BC31441  
  
### Исправление ошибки  
  
1.  Используйте модификатор доступа `Private` в реализации разделяемого метода, как показано в следующем примере.  
  
    ```vb#  
    Private Sub valueChanged() MsgBox(Value was changed to " & Me.Quantity) End Sub  
    ```  
  
## См. также  
 [Разделяемые методы](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Уровни доступа в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)