---
title: "Разделяемые методы должны объявляться как &quot;Private&quot; вместо &quot;&lt;модификаторДоступа&gt;&quot; | Microsoft Docs"
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
  - "vbc31431"
  - "bc31431"
helpviewer_keywords: 
  - "BC31431"
ms.assetid: bbd757f3-7281-4488-8a06-f3b4bcc820dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Разделяемые методы должны объявляться как &quot;Private&quot; вместо &quot;&lt;модификаторДоступа&gt;&quot;
В объявлениях разделяемых методов необходим модификатор доступа `Private`. В приведенном ниже примере показано использование `Private` в сигнатуре метода и его реализации.  
  
```vb#  
' Definition of the partial method signature. Partial Private Sub OnNameChanged() ' The body of the signature is empty. End Sub  
```  
  
```vb#  
' Implementation of the partial method. Private Sub OnNameChanged() MsgBox("Name was changed to " & Me.Name) End Sub  
```  
  
 **Идентификатор ошибки:** BC31431  
  
### Исправление ошибки  
  
-   Измените модификатор доступа на `Private` в объявлениях сигнатуры и реализации.  
  
## См. также  
 [Разделяемые методы](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)