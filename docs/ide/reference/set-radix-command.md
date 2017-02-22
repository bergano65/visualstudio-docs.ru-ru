---
title: "Команда Set Radix | Microsoft Docs"
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
  - "debug.setradix"
helpviewer_keywords: 
  - "Debug.SetRadix - команда"
  - "Задать основание системы счисления - команда"
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда Set Radix
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Устанавливает или возвращает числовой базовый тип, используемый для отображения целочисленных значений.  
  
## Синтаксис  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## Аргументы  
 `10` или `16` или `hex` или `dec`  
 Необязательный.  Указывает десятичную \(10 или dec\) или шестнадцатеричную \(16 или hex\) систему счисления.  Если аргумент отсутствует, возвращается основание текущей системы счисления.  
  
## Пример  
 В приведенном примере устанавливается среда для отображения целочисленных значений в шестнадцатеричном формате.  
  
```  
>Debug.SetRadix hex  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)