---
title: "Ошибка при внедрении манифеста Win32 &lt;манифест&gt; | Microsoft Docs"
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
  - "vbc31191"
  - "bc31191"
helpviewer_keywords: 
  - "BC31191"
ms.assetid: 5babed58-d024-4acd-9838-fab8f07c4a37
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ошибка при внедрении манифеста Win32 &lt;манифест&gt;
Файл, указанный для параметра компилятора `/win32manifest`, не может быть внедрен. Это может быть вызвано недостатком прав на файл манифеста.  
  
 **Идентификатор ошибки:** BC31191  
  
### Исправление ошибки  
  
1.  Убедитесь, что удостоверение, с которым выполняется команда компилятора Visual Basic, имеет доступ к файлу манифеста Win32.  
  
## См. также  
 [\/win32manifest](/dotnet/visual-basic/reference/command-line-compiler/win32manifest)   
 [Компилятор Visual Basic с интерфейсом командной строки](/dotnet/visual-basic/reference/command-line-compiler/index)