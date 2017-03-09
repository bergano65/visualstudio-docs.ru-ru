---
title: "Разрешение вопросов, связанных с исключениями: Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Microsoft.VisualStudio.Tools.Applications.Runtime.ControlNotFoundException - исключение"
ms.assetid: d780b8cc-c3f1-45ed-8f8e-3f8728a4b770
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException
Исключение <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> генерируется, когда <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> не может разобрать строку в соответствии с указанным форматом.  
  
 Свойство `Error Line` объекта исключения содержит текст строки, вызвавшей эту ошибку.  
  
## Полезные советы  
 **Убедитесь, что параметры TextFieldType и Delimiter заданы правильно.**  
 Параметр `TextFieldType` \(ограничение поля разделителями либо поле фиксированной длины\) должен соответствовать формату файла. Если значение `TextFieldType` равно `FixedWidth`, проверьте правильность задания свойства `FieldWidths`. Если значение `TextFieldType` равно `Delimited`, проверьте правильность задания свойства `Delimiters`.  
  
## См. также  
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>   
 [Анализ текстовых файлов с помощью объекта TextFieldParser](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object)   
 [Практическое руководство. Чтение из текстовых файлов с разделителями\-запятыми](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [Практическое руководство. Чтение из текстовых файлов с фиксированной шириной полей](../Topic/How%20to:%20Read%20From%20Fixed-width%20Text%20Files%20in%20Visual%20Basic.md)