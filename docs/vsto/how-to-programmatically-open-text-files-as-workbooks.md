---
title: "Практическое руководство. Программное открытие текстовых файлов как книг Excel | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "текст [разработка решений Office в Visual Studio], текстовые файлы"
  - "текстовые файлы, открытие как книг Excel"
  - "книги, открытие текстовых файлов как"
ms.assetid: 056ae3d0-7fe7-4c28-a2a5-5a948baee0e6
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Практическое руководство. Программное открытие текстовых файлов как книг Excel
  Можно открыть текстовый файл как книгу.  Обязательным параметром является имя открываемого текстового файла.  Необязательными параметрами являются, например, номер первой строки для синтаксического анализа и формат столбцов данных в файле.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Пример  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#80)]  
  
## Компиляция кода  
 Для этого примера требуются следующие компоненты.  
  
-   Текстовый файл с разделителями\-запятыми `Test.txt`, содержащий не менее трех строк.  
  
-   Текстовый файл `Test.txt` должен находиться на диске C.  
  
## См. также  
 [Работа с книгами](../vsto/working-with-workbooks.md)   
 [Практическое руководство. Программное открытие книг Excel](../vsto/how-to-programmatically-open-workbooks.md)   
 [Практическое руководство. Программное создание книг Excel](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Практическое руководство. Программное сохранение книг Excel](../vsto/how-to-programmatically-save-workbooks.md)   
 [Практическое руководство. Программное закрытие книг Excel](../vsto/how-to-programmatically-close-workbooks.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  