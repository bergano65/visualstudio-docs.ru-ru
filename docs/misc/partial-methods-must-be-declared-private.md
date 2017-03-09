---
title: "Частичные методы должны быть объявлены как &quot;Private&quot; | Microsoft Docs"
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
  - "vbc31432"
  - "bc31432"
helpviewer_keywords: 
  - "BC31432"
ms.assetid: 3a4474d9-661e-4793-9624-30cf81faddcf
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Частичные методы должны быть объявлены как &quot;Private&quot;
В объявлениях разделяемых методов необходим модификатор доступа `Private`. В приведенном ниже примере показано использование модификатора `Private` в сигнатуре метода и его реализации.  
  
```vb#  
' Definition of the partial method signature. Partial Private Sub OnNameChanged() ' The body of the signature is empty. End Sub  
```  
  
```vb#  
' Implementation of the partial method. Private Sub OnNameChanged() MsgBox("Name was changed to " & Me.Name) End Sub  
```  
  
 **Идентификатор ошибки:** BC31432  
  
### Исправление ошибки  
  
-   Добавьте ключевое слово `Private` перед `Sub` в объявлениях сигнатуры и реализации.  
  
## См. также  
 [Разделяемые методы](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)