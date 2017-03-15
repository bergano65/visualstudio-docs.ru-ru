---
title: "Операторы &quot;Line&quot; больше не поддерживаются (ошибка компилятора Visual Basic) | Microsoft Docs"
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
  - "vbc30768"
  - "bc30768"
helpviewer_keywords: 
  - "BC30768"
ms.assetid: e7a17c77-06bb-4d33-966e-addb4f51caaf
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операторы &quot;Line&quot; больше не поддерживаются (ошибка компилятора Visual Basic)
Оператор `Line` больше не поддерживается. Функциональность файлового ввода\-вывода обычно доступна как <xref:Microsoft.VisualBasic.FileSystem.LineInput%2A?displayProperty=fullName>, однако целевая версия платформы .NET Compact Framework ее не поддерживает.  
  
 **Идентификатор ошибки:** BC30768  
  
### Исправление ошибки  
  
-   Если выполняется доступ к файлу, используйте функции, определенные в пространстве имен <xref:System.IO>.  
  
-   Если выполняется вывод графики, используйте <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName>.  
  
## См. также  
 <xref:System.IO>   
 <xref:System.Drawing>   
 [Доступ к файлам с помощью Visual Basic](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-access)