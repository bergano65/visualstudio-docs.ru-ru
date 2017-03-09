---
title: "Строка &lt;номер&gt; не может быть проанализирована с помощью текущих разделителей | Microsoft Docs"
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
  - "vbrTextFieldParser_MalFormedDelimitedLine"
ms.assetid: 1f8d4c2d-0334-4da8-acff-5460159835b3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Строка &lt;номер&gt; не может быть проанализирована с помощью текущих разделителей
Указанная строка не может быть проанализирована, так использует разделители, отличные от указанных.  
  
### Исправление ошибки  
  
-   Настройте `Delimiters` так, чтобы строка могла быть проанализирована правильно, или вставьте код обработки исключения, чтобы обработать строку.  
  
## См. также  
 [Практическое руководство. Чтение текстовых файлов различных форматов](../Topic/How%20to:%20Read%20From%20Text%20Files%20with%20Multiple%20Formats%20in%20Visual%20Basic.md)   
 [Метод My.Computer.FileSystem.OpenTextFieldParser](http://msdn.microsoft.com/ru-ru/e5869f85-c078-485f-8323-8dc716494546)   
 [Анализ текстовых файлов с помощью объекта TextFieldParser](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object)   
 [Объект TextFieldParser](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)   
 [Свойство TextFieldParser.Delimiters](http://msdn.microsoft.com/ru-ru/4eb18f4d-3011-40a9-b668-be93eed0444f)   
 [Метод TextFieldParser.SetDelimiters](http://msdn.microsoft.com/ru-ru/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)