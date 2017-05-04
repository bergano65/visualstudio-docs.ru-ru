---
title: "Функция Symbol.for (JavaScript) | Microsoft Docs"
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
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Функция Symbol.for (JavaScript)
Возвращает символ для указанного ключа или, если этот ключ отсутствует, создает новый объект Symbol с новым ключом.  
  
## Синтаксис  
  
```vb  
Symbol.for(key);  
```  
  
#### Параметры  
 `key`  
 Обязательный.  Ключ для символа, который также используется в качестве описания.  
  
## Заметки  
 Этот метод осуществляет поиск символа в реестре глобальных символов.  При сериализации символов в виде строк используйте реестр глобальных символов, чтобы убедиться, что строки сопоставляются с правильными символами во всех случаях.  
  
## Пример  
  
```javascript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]