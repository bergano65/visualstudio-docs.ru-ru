---
title: "Аргумент не может быть Nothing | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrGeneral_ArgumentNullException"
ms.assetid: 2abd995b-36a5-45f0-b3c1-6e0c3b31a875
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Аргумент не может быть Nothing
Для аргумента, который должен иметь значение, предоставлено значение null.  
  
### Исправление ошибки  
  
-   Возможно, была предпринята попытка использовать объект без предоставления экземпляра объекта. В таком случае создайте экземпляр с помощью ключевого слова `New`.  
  
-   Проверьте, что значение вычисляется правильно.  
  
## См. также  
 [Разрешение вопросов, связанных с исключениями: System.NullReferenceException](../Topic/Troubleshooting%20Exceptions:%20System.NullReferenceException.md)