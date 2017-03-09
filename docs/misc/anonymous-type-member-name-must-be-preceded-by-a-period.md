---
title: "Перед именем члена анонимного типа должна стоять точка | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36575"
  - "bc36575"
helpviewer_keywords: 
  - "BC36575"
ms.assetid: b87be29e-39f0-4830-9969-608d71137e3e
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Перед именем члена анонимного типа должна стоять точка
В списке инициализаторов объектов для объявления анонимного типа перед новым именем члена, которому назначается значение, должна быть указана точка. В следующем примере показано правильное и неправильное объявление.  
  
```vb#  
' Valid.  
Dim instanceName1 = New With {.memberName = 10}  
' Invalid declaration that causes this error.  
' Dim instanceName2 = New With {memberName = 10}  
```  
  
 **Идентификатор ошибки:** BC36575  
  
### Исправление ошибки  
  
-   Добавьте точку перед именем члена.  
  
## См. также  
 [Анонимные типы](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)