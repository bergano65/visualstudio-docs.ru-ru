---
title: "Свойства без обязательных параметров не могут объявляться как &quot;Default&quot; | Microsoft Docs"
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
  - "vbc31048"
  - "bc31048"
helpviewer_keywords: 
  - "BC31048"
ms.assetid: 27ef4bc9-532f-4097-a7fc-a645fd5387a3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойства без обязательных параметров не могут объявляться как &quot;Default&quot;
Свойство было указано без обязательных параметров, но с модификатором `Default`.  
  
 **Идентификатор ошибки:** BC31048  
  
### Исправление ошибки  
  
-   Объявите обязательные параметры для свойств по умолчанию.  
  
-   Удалите модификатор `Default` из определения свойства.  
  
## См. также  
 [НЕ В СБОРКЕ. Свойства по умолчанию](http://msdn.microsoft.com/ru-ru/a70f2a27-8176-4858-935e-f25afdd43ab5)