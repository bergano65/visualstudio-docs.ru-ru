---
title: "TextFieldParser не поддерживает токены комментариев, содержащие пробелы. | Microsoft Docs"
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
  - "vbrTextFieldParser_WhitespaceInToken"
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# TextFieldParser не поддерживает токены комментариев, содержащие пробелы.
Представлен токен комментария, содержащий пробел.`TextFieldParser` не поддерживает токены комментариев, содержащие пробелы, если это не пробел в начале токена. Пробелы в начале токена игнорируются.  
  
### Исправление ошибки  
  
-   Укажите правильный токен комментария.  
  
## См. также  
 [Свойство TextFieldParser.CommentTokens](http://msdn.microsoft.com/ru-ru/2e6b6435-4bee-4c14-a353-e8f2c82e2d61)   
 [Анализ текстовых файлов с помощью объекта TextFieldParser](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object)   
 [Объект TextFieldParser](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)