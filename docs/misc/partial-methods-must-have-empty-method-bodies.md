---
title: "Разделяемые методы должны иметь пустые тела методов. | Microsoft Docs"
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
  - "bc31435"
  - "vbc31435"
helpviewer_keywords: 
  - "BC31435"
ms.assetid: 279f283d-ce40-401c-8494-4bf06394fdd3
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Разделяемые методы должны иметь пустые тела методов.
Тело объявления сигнатуры разделяемого метода не должно содержать никакой код. В следующем примере показана сигнатура разделяемого метода и его реализация.  
  
```  
' Definition of the partial method signature. Partial Private Sub OnNameChanged() ' The body of the signature is empty. End Sub  
```  
  
```  
' Implementation of the partial method. Private Sub OnNameChanged() MsgBox("Name was changed to " & Me.Name) End Sub  
```  
  
 **Идентификатор ошибки:** 31435  
  
### Исправление ошибки  
  
-   Удалите любой код из объявления разделяемого метода.  
  
## См. также  
 [Разделяемые методы](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)