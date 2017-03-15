---
title: "Предупреждение командной строки D9042 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "D9042"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9042"
ms.assetid: d710693b-e422-40b2-b2dd-79e1b163b9e6
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение командной строки D9042
Недопустимое значение "значение" параметра "\/параметр"; принято "значение"; в данной версии компилятора отсутствуют предупреждения модуля анализа кода  
  
 Номер предупреждения анализатора кода добавлен в **\/wd**, **\/we**, **\/wo** или параметры командной строки **\/wl** и **\/analyze** указаны в платформе, не поддерживающей анализ кода.  Чтобы удалить это предупреждение, либо перейдите на версию x86 Visual Studio Team System, либо удалите параметр **\/analyze** командной строки.  
  
## Пример  
 Следующий пример командной строки порождает предупреждение D9042 в системах x64 или Itanium:  
  
```  
cl /EHsc /LD /wd6001 /analyze filename.cpp  
```  
  
 Для исправления ошибки перейдите на версию x86 Visual Studio Team System или удалите параметры командной строки **\/analyze** и **\/wd6001**.  
  
## См. также  
 [Ошибки командной строки с D8000 по D9999](/visual-cpp/error-messages/tool-errors/command-line-errors-d8000-through-d9999)   
 [Параметры компилятора](/visual-cpp/build/reference/compiler-options)