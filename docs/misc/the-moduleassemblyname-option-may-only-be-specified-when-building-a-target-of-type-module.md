---
title: "Параметр /moduleassemblyname может указываться только при построении конечного объекта типа &quot;module&quot; | Microsoft Docs"
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
  - "bc2030"
  - "vbc2030"
helpviewer_keywords: 
  - "BC2030"
ms.assetid: 2ebc577b-3464-40cc-8788-9fc9d3b4f928
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр /moduleassemblyname может указываться только при построении конечного объекта типа &quot;module&quot;
Параметр `/moduleassemblyname` был передан компилятору Visual Basic, когда параметр `/target` установлен в значение, отличное от `module`.  
  
 **Идентификатор ошибки:** BC2030  
  
### Исправление ошибки  
  
1.  Удалите параметр компилятора `/moduleassemblyname` либо установите для параметра `/target` значение `module`.  
  
## См. также  
 [\/target](/dotnet/visual-basic/reference/command-line-compiler/target)   
 [\/moduleassemblyname](/dotnet/visual-basic/reference/command-line-compiler/moduleassemblyname)   
 [Компилятор Visual Basic с интерфейсом командной строки](/dotnet/visual-basic/reference/command-line-compiler/index)