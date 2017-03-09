---
title: "Переменная ресурса в Using должна иметь явную инициализацию. | Microsoft Docs"
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
  - "vbc36011"
  - "bc36011"
helpviewer_keywords: 
  - "BC36011"
ms.assetid: 5db996a6-0802-4b67-91f1-4aa9c3dd6b09
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Переменная ресурса в Using должна иметь явную инициализацию.
Инструкция `Using` указывает по крайней мере один ресурс, который не инициализируется с помощью предложения `New`.  
  
 Если вы еще не получили ресурс до передачи управления в блок `Using`, инструкция `Using` должна получить ресурс. Для этого необходимо создать объект из указанного класса, что требует предложения `New`.  
  
 **Идентификатор ошибки:** BC36011  
  
### Исправление ошибки  
  
-   Если ресурс уже получен, используйте ссылочную переменную или выражение в инструкции `Using`, которая оценивается как полученный ресурс.  
  
     `Dim newFont As New System.Drawing.Font`  
  
     `Using newFont`  
  
-   Если ресурс еще не получен, добавьте в инструкцию `Using` предложение `New`.  
  
     `Using newFont as`   `New`   `System.Drawing.Font`  
  
## См. также  
 [Оператор Using](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [Оператор New](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Практическое руководство. Удаление системного ресурса](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)