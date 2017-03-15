---
title: "Параметр /win32manifest пропускается | Microsoft Docs"
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
  - "vbc2034"
  - "bc2034"
helpviewer_keywords: 
  - "BC2034"
ms.assetid: 8009553a-f6ba-4d2b-8ddd-8a9357bc928e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр /win32manifest пропускается
Параметр \/win32manifest игнорируется. Он может быть задан, только если целевым объектом является сборка.  
  
 Параметр `/win32manifest` был передан компилятору Visual Basic, когда параметр `/target` установлен в значение `module`.  
  
 **Идентификатор ошибки:** BC2034  
  
### Исправление ошибки  
  
1.  Удалите параметр компилятора `/win32manifest` либо установите для параметра `/target` значение `exe`, `winexe` или `library`.  
  
## См. также  
 [\/target](/dotnet/visual-basic/reference/command-line-compiler/target)   
 [\/win32manifest](/dotnet/visual-basic/reference/command-line-compiler/win32manifest)   
 [Компилятор Visual Basic с интерфейсом командной строки](/dotnet/visual-basic/reference/command-line-compiler/index)