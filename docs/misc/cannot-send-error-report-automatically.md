---
title: "нельзя отправить отчет об ошибках автоматически | Microsoft Docs"
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
  - "bc2027"
  - "vbc2027"
helpviewer_keywords: 
  - "BC2027"
ms.assetid: 84ba8580-2234-46d1-b4a5-94b03f64c0c7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# нельзя отправить отчет об ошибках автоматически
нельзя отправить отчет об ошибках автоматически. Перейдите на "http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039" для настройки параметров отправки отчета об ошибках.  
  
 Указан параметр компилятора `/errorreport:send`, но компьютер не настроен для автоматической отправки отчетов об ошибках. Сведения о внутренних ошибках в компиляторе Visual Basic отправляться не будут.  
  
 **Идентификатор ошибки:** BC2027  
  
### Исправление ошибки  
  
-   Удалите параметр компилятора `/errorreport:send` либо замените его на `/errorreport:queue`, `/errorreport:prompt` или `/errorreport:none`.  
  
     — или —  
  
-   Включите автоматические отчеты об ошибках, следуя инструкциям на странице [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039](http://go.microsoft.com/fwlink/?LinkId=42039).  
  
## См. также  
 [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport)   
 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039](http://go.microsoft.com/fwlink/?LinkId=42039)