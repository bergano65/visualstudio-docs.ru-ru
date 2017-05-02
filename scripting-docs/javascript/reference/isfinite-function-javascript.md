---
title: "Функция isFinite (JavaScript) | Microsoft Docs"
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
  - "isFinite"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "конечные числа"
  - "isFinite - метод"
ms.assetid: ea9287d2-892f-496b-86b7-f9196868d5cf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Функция isFinite (JavaScript)
Определяет, является ли указанное число конечным.  
  
## Синтаксис  
  
```  
isFinite(number)   
```  
  
## Заметки  
 Обязательный аргумент `number` представляет собой любое числовое значение.  
  
 Функция `isFinite` возвращает значение `true`, если `number` имеет любое значение, отличное от `NaN`, отрицательной бесконечности или положительной бесконечности.  В последних трех случаях возвращается значение **false**.  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Global](../../javascript/reference/global-object-javascript.md)  
  
## См. также  
 [Функция isNaN](../../javascript/reference/isnan-function-javascript.md)