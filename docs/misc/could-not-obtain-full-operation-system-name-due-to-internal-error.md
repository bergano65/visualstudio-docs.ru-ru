---
title: "Не удалось получить полное имя операционной системы из-за внутренней ошибки | Microsoft Docs"
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
  - "vbrDiagnosticInfo_FullOSName"
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удалось получить полное имя операционной системы из-за внутренней ошибки
Не удалось получить полное имя операционной системы из\-за внутренней ошибки. Это может быть вызвано отсутствием WMI на текущем компьютере.  
  
 Не удалось выполнить вызов свойства `My.Computer.Info.OSFullName`. Возможная причина этой ошибки может заключаться в том, что на текущем компьютере не установлен инструментарий управления Windows \(WMI\).  
  
### Исправление ошибки  
  
1.  Добавьте блок `Try...Catch` вокруг вызова свойства `My.Computer.Info.OSFullName`.  
  
2.  Чтобы получить дополнительные сведения об инструментарии WMI и его установке, перейдите на веб\-сайт  и выполните поиск по ключевым словам "Основы инструментария управления Windows \(WMI\)".  
  
## См. также  
 [Свойство My.Computer.Info.OSFullName](http://msdn.microsoft.com/ru-ru/b3b0fbd1-4dc5-428a-ad04-0d9fc9c2a9be)   
 [Обработка исключений и ошибок в Visual Basic](http://msdn.microsoft.com/ru-ru/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)