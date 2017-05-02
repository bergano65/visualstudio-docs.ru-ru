---
title: "Условная компиляция отключена | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Условная компиляция отключена
Предпринята попытка использования переменной условной компиляции без предварительного включения условной компиляции.  При включении условной компиляции компилятор [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] начинает интерпретировать идентификаторы, которые начинаются с символа @, как переменные условной компиляции.  Это можно сделать, начав условный код следующим оператором:  
  
```  
/*@cc_on @*/  
```  
  
### Исправление ошибки  
  
-   Добавьте следующий оператор в начало условного кода.  
  
    ```javascript  
    /*@cc_on @*/  
    ```  
  
## См. также  
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [Оператор @cc\_on](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [Оператор @if](../../javascript/reference/at-if-statement-javascript.md)   
 [Оператор @set](../../javascript/reference/at-set-statement-javascript.md)