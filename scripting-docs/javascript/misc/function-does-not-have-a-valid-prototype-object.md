---
title: "Для функции отсутствует допустимый объект-прототип | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Для функции отсутствует допустимый объект-прототип
Предпринята попытка использовать метод **instanceof**, чтобы проверить, является ли объект производным от определенного класса функции, однако свойство `prototype` этого объекта было переопределено и ему назначено значение `null` или тип внешнего объекта \(оба этих значения не являются допустимыми объектами [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\).  Внешний объект может принадлежать объектной модели главного окна \(например, документ Internet Explorer или объект\-окно\) или представлять собой COM\-объект.  
  
### Исправление ошибки  
  
-   Убедитесь, что свойство `prototype` функции ссылается на допустимый объект [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## См. также  
 [Объект Function](../../javascript/reference/function-object-javascript.md)   
 [Свойство prototype \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)