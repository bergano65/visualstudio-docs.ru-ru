---
title: "Не обнаружена мышь. | Microsoft Docs"
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
  - "vbrMouse_NoMouseIsPresent"
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не обнаружена мышь.
Было вызвано одно из свойств объекта `My.Computer.Mouse`, но на компьютере отсутствует установленная мышь или порт мыши.  
  
### Исправление ошибки  
  
-   Добавьте блок `Try...Catch` вокруг вызова свойства объекта `My.Computer.Mouse`.  
  
     Или...  
  
-   Установите мышь на компьютере.  
  
## См. также  
 [Объект My.Computer.Mouse](/dotnet/visual-basic/language-reference/objects/my-computer-mouse-object)   
 [Обработка исключений и ошибок в Visual Basic](http://msdn.microsoft.com/ru-ru/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)