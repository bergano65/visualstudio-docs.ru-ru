---
title: "Ожидался символ &quot;@&quot; | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1032"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Ожидался символ &quot;@&quot;
Предпринята попытка создать переменную для использования с операторами условной компиляции с помощью оператора `@set`, но отсутствует знак **@** перед именем переменной.  
  
### Исправление ошибки  
  
-   Добавьте знак **@**непосредственно перед именем переменной.  Примеры.  
  
    ```javascript  
    @set @myvar = 1  
    ```  
  
## См. также  
 [Оператор @set](../../javascript/reference/at-set-statement-javascript.md)   
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)