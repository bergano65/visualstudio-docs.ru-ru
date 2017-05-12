---
title: "В регулярном выражении ожидался символ &quot;]&quot; (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# В регулярном выражении ожидался символ &quot;]&quot; (JavaScript)
Предпринята попытка создать класс символов для сопоставления регулярных выражений, но не поставлена квадратная скобка.  Сочетания отдельных символов\-литералов можно собирать в классы символов, размещая их внутри квадратных скобок.  Класс символов соответствует любому содержащемуся в нем символу.  Например, \/\[abc\]\/ соответствует любой из букв "a", "b" или "c".  
  
### Исправление ошибки  
  
-   Добавьте в регулярное выражение правую квадратную скобку.  
  
    > [!NOTE]
    >  Если требуется сопоставить одну квадратную скобку, необходимо предварить ее обратной косой чертой — \\\[ — чтобы она не интерпретировалась [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] как специальный символ.  
  
## См. также  
 [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)