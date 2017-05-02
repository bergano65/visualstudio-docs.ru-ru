---
title: "Метод toLocaleString (Object) (JavaScript) | Microsoft Docs"
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
  - "toLocaleString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleString - метод"
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Метод toLocaleString (Object) (JavaScript)
Возвращает дату, преобразованную в строку с использованием текущего языкового стандарта.  
  
## Синтаксис  
  
```  
  
dateObj.toLocaleString()   
```  
  
## Заметки  
 Обязательный аргумент `dateObj` представляет собой любой объект `Date`.  
  
 Метод `toLocaleString` возвращает объект `String`, который содержит дату, записанную в длинном формате, принятом по умолчанию в текущем языковом стандарте.  
  
-   Для дат в диапазоне от 1601 до 1999 года нашей эры даты форматируются в соответствии с региональными стандартами, заданными в панели управления пользователя.  
  
-   Для дат за пределами этого диапазона используется формат метода **toString** по умолчанию.  
  
 Например, в Соединенных Штатах для 5 января метод `toLocaleString` возвращает значение "01\/05\/96 00:00:00".  В Европе для этой же даты он возвращает значение "05\/01\/96 00:00:00", потому что в европейской традиции дата ставится перед месяцем.  
  
> [!NOTE]
>  Метод `toLocaleString` следует использовать только для отображения результатов для пользователя; его нельзя использовать в качестве основы для вычислений в скрипте, поскольку возвращаемый результат зависит от конкретного компьютера.  
  
## Пример  
 В следующем примере показано использование метода `toLocaleString`.  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Array](../../javascript/reference/array-object-javascript.md)&#124; [Объект Date](../../javascript/reference/date-object-javascript.md)&#124; [Объект Number](../../javascript/reference/number-object-javascript.md)&#124; [Объект Object](../../javascript/reference/object-object-javascript.md)  
  
## См. также  
 [Метод toLocaleDateString \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)