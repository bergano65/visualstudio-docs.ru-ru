---
title: "Операторы Get больше не поддерживаются (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30767"
  - "bc30767"
helpviewer_keywords: 
  - "BC30767"
ms.assetid: 6aa62dcc-99aa-4051-a81e-3bbb6a8c355f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операторы Get больше не поддерживаются (Visual Basic)
Операторы `Get` больше не поддерживаются. Функциональные возможности файлового ввода\-вывода обычно предоставляются пространством имен `Microsoft.VisualBasic`, однако целевая платформа .NET Compact Framework его не поддерживает.  
  
 **Идентификатор ошибки:** BC30767  
  
### Исправление ошибки  
  
-   Выполните операции с файлами с помощью функций, определенных в пространстве имен <xref:System.IO>.  
  
## См. также  
 <xref:System.IO>   
 [Оператор Get](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Доступ к файлам с помощью Visual Basic](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-access)