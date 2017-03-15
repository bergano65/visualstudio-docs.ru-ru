---
title: "Переменная ресурса в операторе Using не может быть массивом. | Microsoft Docs"
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
  - "vbc36012"
  - "bc36012"
helpviewer_keywords: 
  - "BC36012"
ms.assetid: f98c54b0-6ede-48b6-aa31-438664c219f3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Переменная ресурса в операторе Using не может быть массивом.
Оператор `Using` задает переменную массива для ресурса.  
  
 Класс <xref:System.Array> не реализует интерфейс <xref:System.IDisposable>, поэтому блок `Using` не может вызвать метод <xref:System.IDisposable.Dispose%2A> в ресурсе массива.  
  
 **Идентификатор ошибки:** BC36012  
  
### Исправление ошибки  
  
-   Используйте другой тип системного ресурса в блоке `Using`.  
  
## См. также  
 [Оператор Using](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [Практическое руководство. Удаление системного ресурса](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. Обзор массивов в Visual Basic](http://msdn.microsoft.com/ru-ru/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)