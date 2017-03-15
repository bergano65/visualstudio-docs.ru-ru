---
title: "Разрешение вопросов, связанных с исключениями: System.IO.IOException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IOException - класс"
ms.assetid: 87812daa-0784-43dc-b3dc-6652a960c362
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.IO.IOException
Исключение <xref:System.IO.IOException> возникает, когда происходит ошибка ввода\-вывода, такая как сбой чтения или записи файла.  
  
## Полезные советы  
 **Убедитесь, что существуют файл и каталог.**  
 Убедитесь, что каталог, в который производится попытка записи или чтения, существует. Убедитесь, что считываемый файл существует.  
  
### Примечания  
 Класс <xref:System.IO.IOException> является базовым классом для исключений, возникающих при доступе к данным с помощью потоков, файлов и каталогов.  
  
 Библиотека базовых классов включает следующие типы, каждый из которых является производным классом класса <xref:System.IO.IOException>:  
  
-   <xref:System.IO.DirectoryNotFoundException>  
  
-   <xref:System.IO.EndOfStreamException>  
  
-   <xref:System.IO.FileNotFoundException>  
  
-   <xref:System.IO.FileLoadException>  
  
-   <xref:System.IO.PathTooLongException>  
  
## См. также  
 <xref:System.IO.IOException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [NOTINBUILD Практическое руководство. Создание консольного приложения CLR](http://msdn.microsoft.com/ru-ru/b8af4197-e65f-4b17-b18e-b9e92965d026)