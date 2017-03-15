---
title: "Нельзя одновременно задать /win32icon и /win32resource | Microsoft Docs"
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
  - "vbc2023"
  - "bc2023"
helpviewer_keywords: 
  - "BC2023"
ms.assetid: 60914807-1fde-4fef-9c6f-6f4a62527eed
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Нельзя одновременно задать /win32icon и /win32resource
Параметры `/win32resource` и `/win32icon` являются взаимоисключающими, поскольку они оба вставляют информацию о значках в выходной файл.  
  
 **Идентификатор ошибки:** BC2023  
  
### Исправление ошибки  
  
-   Используйте только `/win32icon` для вставки ICO\-файла в выходной файл. Этот ICO\-файл представляет выходной файл в проводнике Windows.  
  
     Или...  
  
-   Используйте только вариант `/win32resource` для вставки файла ресурсов Win32 в выходной файл. Ресурс Win32 может содержать сведения о версии или точечный рисунок \(значок\) для упрощения идентификации приложения в проводнике.  
  
## См. также  
 [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon)   
 [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource)