---
title: "Команда Print | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.print"
helpviewer_keywords: 
  - "Debug.Print - команда"
  - "Печать - команда"
  - "Print - метод"
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда Print
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Вычисление выражения или отображение указанного текста.  
  
## Синтаксис  
  
```  
Debug.Print text  
```  
  
## Аргументы  
 `text`  
 Обязательный.  Выражение для вычисления или текст для отображения.  
  
## Заметки  
 В качестве псевдонима этой команды можно использовать вопросительный знак \(?\).  Так, например, команда  
  
```  
>Debug.Print expA  
```  
  
 может также выглядеть следующим образом:  
  
```  
>? expA  
```  
  
 Оба варианта этой команды возвращают текущее значение выражения `expA`.  
  
## Пример  
  
```  
>Debug.Print varA  
```  
  
## См. также  
 [Команда Evaluate Statement](../../ide/reference/evaluate-statement-command.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)