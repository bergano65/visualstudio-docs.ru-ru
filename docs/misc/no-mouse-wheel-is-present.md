---
title: "Не обнаружено колесо мыши | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrMouse_NoWheelIsPresent"
ms.assetid: e924ffba-4af1-4247-9a6f-d19a03738f62
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не обнаружено колесо мыши
Было вызвано свойство `My.Computer.Mouse.WheelScrollLines`, но у мыши отсутствует колесо прокрутки.  
  
### Исправление ошибки  
  
-   Проверьте свойство `My.Computer.Mouse.WheelExists`, чтобы увидеть, имеется ли колесо прокрутки мыши, перед вызовом свойства `My.Computer.Mouse.WheelScrollLines`.  
  
     \-или\-  
  
-   Установите на компьютере мышь с колесом прокрутки.  
  
## См. также  
 [Свойство My.Computer.Mouse.WheelScrollLines](http://msdn.microsoft.com/ru-ru/67600f96-25d7-4dd9-946a-b46e1fc6a57f)   
 [Свойство My.Computer.Mouse.WheelExists](http://msdn.microsoft.com/ru-ru/332d44f7-0b66-4eaa-b4ce-d7f161bfbd07)   
 [Обработка исключений и ошибок в Visual Basic](http://msdn.microsoft.com/ru-ru/3e351e73-cf23-40ab-8b60-05794160529e)