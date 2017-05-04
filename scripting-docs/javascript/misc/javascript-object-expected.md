---
title: "Ожидается объект JavaScript | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5014"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: cc7cc32b-e444-4afa-9be1-802c83fdf5ae
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Ожидается объект JavaScript
Предпринята попытка передать объект, не являющийся объектом [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], во встроенную функцию, которая ожидает объект [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Различные встроенные функции требуют объектов, определенных в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] \(в отличие от объектов, определенных основным приложением или в внешним компонентом, таким как элемент управления\).  
  
### Исправление ошибки  
  
-   Убедитесь, что объект, который передается в качестве параметра, имеет правильный тип.  
  
## См. также  
 [Объекты и массивы](../../javascript/objects-and-arrays-javascript.md)   
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)