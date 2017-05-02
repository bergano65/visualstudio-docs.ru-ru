---
title: "Свойство Debug.setNonUserCodeExceptions | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Свойство Debug.setNonUserCodeExceptions
Определяет, есть ли в этой области блоки try\-catch, которые должны быть рассмотрены отладчиком, как не обрабатываемые пользовательским кодом.  Исключения можно разделить на создаваемые, не обрабатываемые пользовательским кодом или необрабатываемые.  
  
 Если это свойство имеет значение `true` в данной области, отладчик может выполнить некоторое действие \(например, приостановить\) над исключениям, появившимися внутри области, если разработчик хочет прервать выполнение на исключениях, не обрабатываемых пользовательским кодом.  Если это свойство имеет значение `false`, это то же, как если бы это свойство никогда не было задано.  
  
 Дополнительные сведения по отладке см. в разделе [Обзор отладки активных скриптов](http://go.microsoft.com/fwlink/p/?LinkId=249469).  
  
## Синтаксис  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## Пример  
 В следующем коде показано, как задать это свойство.  
  
```javascript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]