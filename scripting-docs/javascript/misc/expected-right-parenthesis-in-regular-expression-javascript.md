---
title: "В регулярном выражении ожидался символ &quot;)&quot; (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5020"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# В регулярном выражении ожидался символ &quot;)&quot; (JavaScript)
Предпринята попытка создать запись, утверждение или группу регулярных выражений, но не поставлена закрывающая круглая скобка.  Круглые скобки используются в регулярных выражениях несколькими способами.  В основном они используются для записи частей выражений, для указания утверждений или для группирования шаблонов так, чтобы элементы воспринимались как одна единица операторами \*, \+, ? и т. п.  
  
### Исправление ошибки  
  
-   Добавьте крайнюю правую закрывающую круглую скобку.  
  
    > [!NOTE]
    >  Если требуется сопоставить одну круглую скобку, необходимо предварить ее обратной косой чертой — \\\( — чтобы она не интерпретировалась [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] как специальный символ.  
  
## См. также  
 [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)