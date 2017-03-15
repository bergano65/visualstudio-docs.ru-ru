---
title: "Параметр &quot;&lt;имя_параметра&gt;&quot; метода расширения &quot;&lt;имя_метода&gt;&quot;, определенного в &quot;&lt;имя_типа&gt;&quot;, уже содержит соответствующий опущенный аргумент | Microsoft Docs"
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
  - "bc36583"
  - "vbc36583"
helpviewer_keywords: 
  - "BC36583"
ms.assetid: 662072fa-abb8-43c3-8ca2-aefb20f2e902
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр &quot;&lt;имя_параметра&gt;&quot; метода расширения &quot;&lt;имя_метода&gt;&quot;, определенного в &quot;&lt;имя_типа&gt;&quot;, уже содержит соответствующий опущенный аргумент
При вызове процедурой метода расширения указывается аргумент по позиции, а затем тот же аргумент указывается по имени. Например, в следующем вызове метода расширения `ABC` сначала указывается аргумент для параметра `Y`, а затем он же указывается по имени.  
  
```  
<Extension()> _ Public Sub ABC(ByVal X As Integer, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) End Sub ' . . . ' Calling extension method ABC. Dim number As Integer ' Not valid. ' number.ABC(, 4, Y:=5)  
```  
  
 **Идентификатор ошибки:** BC36583  
  
### Исправление ошибки  
  
-   Задайте аргумент по позиции или удалите запятую, которая указывает на пропуск аргумента.  
  
## См. также  
 [Методы расширения](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Передача аргументов по позиции и по имени](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)