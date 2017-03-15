---
title: "Не удается получить сведения о памяти из-за внутренней ошибки. | Microsoft Docs"
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
  - "vbrDiagnosticInfo_Memory"
ms.assetid: 1ba8f774-5858-438e-914e-99fddc9e5e7e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается получить сведения о памяти из-за внутренней ошибки.
Вызов одного из свойств сведений о памяти объекта `My.Computer.Info` завершился неудачно.  
  
### Исправление ошибки  
  
-   Добавьте блок `Try...Catch` вокруг вызова свойства сведений о памяти объекта `My.Computer.Info`.  
  
## См. также  
 [Объект My.Computer.Info](/dotnet/visual-basic/language-reference/objects/my-computer-info-object)   
 [Обработка исключений и ошибок в Visual Basic](http://msdn.microsoft.com/ru-ru/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)