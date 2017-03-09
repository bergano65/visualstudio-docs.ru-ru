---
title: "Не удается прочитать поля с разделителями, поскольку двойные кавычки не являются допустимым разделителем, если параметр EscapeQuotes имеет значение True | Microsoft Docs"
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
  - "vbrTextFieldParser_IllegalDelimiter"
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается прочитать поля с разделителями, поскольку двойные кавычки не являются допустимым разделителем, если параметр EscapeQuotes имеет значение True
`TextFieldParser` не может читать из файла, поскольку в качестве разделителя указан знак кавычек \("\), а `EscapeQuotes` имеет значение `True`.  
  
### Исправление ошибки  
  
-   Присвойте свойству `EscapeQuotes` значение `False`.  
  
## См. также  
 [Метод TextFieldParser.SetDelimiters](http://msdn.microsoft.com/ru-ru/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)   
 [Свойство TextFieldParser.Delimiters](http://msdn.microsoft.com/ru-ru/4eb18f4d-3011-40a9-b668-be93eed0444f)   
 [Практическое руководство. Чтение из текстовых файлов с разделителями\-запятыми](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [Объект TextFieldParser](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)