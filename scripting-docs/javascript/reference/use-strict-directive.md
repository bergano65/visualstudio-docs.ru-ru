---
title: "Директива use strict | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "strict_JavaScriptKeyword"
  - "use strict"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "строгий режим"
  - "use strict - директива"
  - "use strict"
ms.assetid: b532e8c9-548c-4bbe-b2fc-5459ebd62e56
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Директива use strict
Ограничивает использование некоторых функций в JavaScript.  Поддерживается только в Internet Explorer 10 и в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Синтаксис  
  
```javascript  
use strict  
```  
  
## Заметки  
  
## Пример  
 Следующий код вызывает синтаксическую ошибку, поскольку в строгом режиме необходимо объявить все переменные с `var`.  
  
```javascript  
"use strict";  
function testFunction(){  
   var testvar = 4;  
    return testvar;  
}  
intvar = 5;  
  
```  
  
## См. также  
 [Строгий режим](../../javascript/advanced/strict-mode-javascript.md)