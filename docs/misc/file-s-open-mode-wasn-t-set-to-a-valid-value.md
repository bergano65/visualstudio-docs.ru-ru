---
title: "Для режима открытия файла не было задано правильное значение | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 969541f6-9ff6-4804-ba61-0d17370060ef
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Для режима открытия файла не было задано правильное значение
Значение, указанное для режима открытия файла, недопустимо. В следующей таблице показаны допустимые значения перечисления <xref:Microsoft.VisualBasic.OpenMode>.  
  
|Значение|Режим|  
|--------------|-----------|  
|1|`OpenMode.Input`|  
|2|`OpenMode.Output`|  
|4|`OpenMode.Random`|  
|8|`OpenMode.Append`|  
|32|`OpenMode.Binary`|  
  
### Исправление ошибки  
  
-   Убедитесь, что для режима открытия файла указывается значение.  
  
## См. также  
 [НЕ В СБОРКЕ. Перечисление OpenMode](http://msdn.microsoft.com/ru-ru/e995bd42-d11f-455c-88c4-308345172633)   
 [Объект My.Computer.FileSystem](/dotnet/visual-basic/language-reference/objects/my-computer-filesystem-object)   
 [Чтение из файлов](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/reading-from-files)   
 [Запись в файлы](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/writing-to-files)