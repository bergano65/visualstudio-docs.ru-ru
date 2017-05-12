---
title: "Оператор return за пределами функции | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Оператор return за пределами функции
Оператор `return` использован в глобальной области кода.  Оператор `return` следует использовать только внутри тела функции.  
  
 Вызов функции с помощью оператора `()` представляет собой выражение.  Все выражения имеют значения; оператор `return` используется для указания значения, возвращаемого функцией.  Общая форма следующая:  
  
```  
  
return [ expression ];  
```  
  
 При выполнении оператора `return` значение *выражения* вычисляется и возвращается в качестве значения функции.  Если выражение отсутствует, возвращается значение **undefined**.  
  
 При выполнении оператора `return` выполнение функции останавливается, даже если в теле функции остались другие операторы.  Исключением из этого правила является наличие оператора **return** в блоке **try**, для которого указан соответствующий блок **finally**. В этом случае перед завершением работы функции выполняется код в блоке **finally**.  
  
 Если функция завершает работу из\-за достижения конца тела функции без выполнения оператора `return`, возвращается значение **undefined** \(это означает, что результат функции нельзя использовать в составе большего выражения\).  
  
### Исправление ошибки  
  
-   Удалите оператор `return` из основной части кода \(глобальной области\).  
  
## См. также  
 [Оператор return](../../javascript/reference/return-statement-javascript.md)   
 [Объект Function](../../javascript/reference/function-object-javascript.md)   
 [Свойство caller \(Function\)](../../javascript/reference/caller-property-function-javascript.md)