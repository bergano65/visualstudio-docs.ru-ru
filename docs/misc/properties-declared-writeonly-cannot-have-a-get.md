---
title: "Свойства, объявленные как WriteOnly, не могут иметь процедуру Get. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30023"
  - "vbc30023"
helpviewer_keywords: 
  - "BC30023"
ms.assetid: ac290f7d-cbc3-4979-a5d9-1ae1bb26e79d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойства, объявленные как WriteOnly, не могут иметь процедуру Get.
Процедура `Get` читает значение свойства. Чтение свойств `WriteOnly` невозможно.  
  
 **Идентификатор ошибки:** BC30023  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `WriteOnly` из оператора `Property` или удалите процедуру `Get` из тела свойства.  
  
## См. также  
 [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Оператор Get](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [WriteOnly](/dotnet/visual-basic/language-reference/modifiers/writeonly)