---
title: "Длина массива должна быть конечным положительным целым числом | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Длина массива должна быть конечным положительным целым числом
При задании свойства **length** существующего объекта **Array** указана длина массива, которая не является положительным числом или нулем.  Эта ошибка возникает при присвоении свойству **length** объекта `Array` значения, которое является отрицательным числом или не является числом \(`NaN`\).  Обратите внимание, что [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] автоматически преобразует дробные числа в целые.  
  
### Исправление ошибки  
  
-   Присвойте свойству длины положительное целое число.  Верхнего ограничения на размер массива не существует, кроме максимально возможного значения целого числа \(приблизительно 4 миллиарда\).  В следующем примере показан правильный способ задания свойства **length** объекта **Array** .  
  
    ```javascript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## См. также  
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)