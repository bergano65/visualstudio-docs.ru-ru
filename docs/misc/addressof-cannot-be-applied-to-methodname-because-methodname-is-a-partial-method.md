---
title: "AddressOf не может применяться к методу &quot;имя_метода&quot;, так как &quot;имя_метода&quot; является разделяемым методом | Microsoft Docs"
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
  - "vbc31440"
  - "bc31440"
helpviewer_keywords: 
  - "BC31440"
ms.assetid: 924dbada-3e0a-4004-a3ae-a209b7c3d1fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# AddressOf не может применяться к методу &quot;имя_метода&quot;, так как &quot;имя_метода&quot; является разделяемым методом
Разделяемый метод передан в оператор `AddressOf`. Разделяемые методы являются недопустимыми значениями для оператора `AddressOf`.  
  
 **Идентификатор ошибки:** BC31440  
  
### Исправление ошибки  
  
1.  Добавьте метод реализации для разделяемого метода. Метод реализации является допустимым значением для оператора `AddressOf`. В следующем примере показана сигнатура разделяемого метода и его реализация.  
  
    ```vb#  
    ' Definition of the partial method signature.  
    Partial Private Sub OnNameChanged()  
        ' The body of the signature is empty.  
    End Sub  
  
    ' Implementation of the partial method.  
    Private Sub OnNameChanged()  
        MsgBox("Name was changed to " & Me.Name)  
    End Sub  
    ```  
  
## См. также  
 [Оператор AddressOf](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Разделяемые методы](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)