---
title: "Свойство caller (Function) (JavaScript) | Microsoft Docs"
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
  - "caller"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "caller - свойство"
  - "вызовы функций, выполняющиеся функции"
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Свойство caller (Function) (JavaScript)
Получает функцию, вызвавшую текущую функцию.  
  
## Синтаксис  
  
```  
  
functionName.caller  
```  
  
## Заметки  
 Объект `functionName` представляет собой имя любой выполняемой функции.  
  
 Свойство `caller` определено для функции только на время ее выполнения.  Если функция вызывается из верхнего уровня программы [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], свойство `caller` содержит значение `null`.  
  
 Если свойство `caller` используется в строковом контексте, результат совпадает со строкой `functionName`.`toString`, то есть отображается декомпилированный текст функции.  
  
 В следующем примере показано использование свойства `caller`.  
  
```javascript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## См. также  
 [Оператор function](../../javascript/reference/function-statement-javascript.md)