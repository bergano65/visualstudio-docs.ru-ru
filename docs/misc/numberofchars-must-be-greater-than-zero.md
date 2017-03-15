---
title: "Значение NumberOfChars должно быть больше нуля | Microsoft Docs"
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
  - "vbrTextFieldParser_NumberOfCharsMustBePositive"
ms.assetid: 3eea4bbf-cd49-4d19-adfb-0e2adf087065
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Значение NumberOfChars должно быть больше нуля
При использовании метода `PeekChars` объекта `TextFieldParser` необходимо указать значение `NumberOfChars` больше `0`.  
  
### Исправление ошибки  
  
-   Измените значение `NumberOfChars` на значение больше `0`.  
  
## См. также  
 [Практическое руководство. Чтение текстовых файлов различных форматов](../Topic/How%20to:%20Read%20From%20Text%20Files%20with%20Multiple%20Formats%20in%20Visual%20Basic.md)   
 [Метод My.Computer.FileSystem.OpenTextFieldParser](http://msdn.microsoft.com/ru-ru/e5869f85-c078-485f-8323-8dc716494546)   
 [Метод TextFieldParser.PeekChars](http://msdn.microsoft.com/ru-ru/4a180d26-d46d-4cc1-9af7-d23abe27c89b)   
 [Анализ текстовых файлов с помощью объекта TextFieldParser](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object)   
 [Объект TextFieldParser](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)