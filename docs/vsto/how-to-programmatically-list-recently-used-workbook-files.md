---
title: "Практическое руководство. Программный вывод списка последних использовавшихся файлов книг Excel | Microsoft Docs"
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
  - "Excel [разработка решений Office в Visual Studio], список недавно использовавшихся файлов"
  - "список последних файлов, Excel"
  - "RecentFiles - свойство"
  - "книги, список недавно использовавшихся"
ms.assetid: 210a3753-4845-4875-b34a-a30d3a1299b3
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Практическое руководство. Программный вывод списка последних использовавшихся файлов книг Excel
  Свойство <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> возвращает коллекцию имен всех файлов из списка недавно использовавшихся файлов Microsoft Office Excel.  Длина списка меняется в зависимости от указанного пользователем количества запоминаемых файлов.  Результаты можно вывести в диапазон.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Вывод списка недавно использовавшихся книг элементе управления NamedRange  
  
1.  Выполните цикл по списку недавно использовавшихся файлов и выведите их имена в ячейки объекта <xref:Microsoft.Office.Interop.Excel.Range>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#9)]  
  
## См. также  
 [Работа с книгами](../vsto/working-with-workbooks.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  