---
title: "Практическое руководство. Программное удаление листов из книг | Microsoft Docs"
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
  - "книги, удаление листов"
  - "листы, удаление"
ms.assetid: c5ae99f0-806d-4320-a29c-75ad444fb996
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Практическое руководство. Программное удаление листов из книг
  В книге можно удалить любой лист.  Для удаления листа используйте ведущий элемент листа или получите доступ к листу с помощью коллекции листов книги.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Использование ведущего элемента листа  
 Если лист был добавлен в настройку на уровне документа во время разработки, для удаления указанного листа используйте метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>.  Следующий код удаляет лист из книги с помощью прямой ссылки на ведущий элемент листа.  
  
> [!IMPORTANT]  
>  Этот код выполняется только в тех проектах, которые создаются с помощью любого из следующих шаблонов проекта:  
>   
>  -   Книга Excel 2013  
> -   Шаблон Excel 2013  
> -   Книга Excel 2010  
> -   Шаблон Excel 2010  
>   
>  Если эту задачу требуется выполнить в проекте любого другого типа, необходимо добавить ссылку на сборку **Microsoft.Office.Interop.Excel**, а затем использовать классы из этой сборки, чтобы открыть книгу и удалить лист.  Дополнительные сведения см. в разделе[Практическое руководство. Обращение к приложениям Office с помощью основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) и [Справочник по основной сборке взаимодействия для Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
#### Удаление листа с помощью ведущего элемента листа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> типа `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#17)]  
  
## Использование коллекции листов книги Excel  
 Обращайтесь к листам с помощью коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> для Microsoft Office Excel в следующих случаях.  
  
-   Требуется удалить лист в надстройке VSTO.  
  
-   Лист, который требуется удалить, был создан во время выполнения в настройке на уровне документа.  
  
 Следующий код удаляет лист из книги с помощью ссылки на лист при использовании номера индекса коллекции **Sheets**.  В этом коде предполагается, что новый лист был создан программным образом.  
  
> [!IMPORTANT]  
>  Если эту задачу требуется выполнить в проекте любого другого типа, необходимо добавить ссылку на сборку **Microsoft.Office.Interop.Excel**, а затем использовать классы из этой сборки, чтобы открыть книгу и удалить лист.  Дополнительные сведения см. в разделе[Практическое руководство. Обращение к приложениям Office с помощью основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) и [Справочник по основной сборке взаимодействия для Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
#### Удаление листа с помощью коллекции листов книги Excel  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Sheets>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#18)]  
  
## См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Практическое руководство. Программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Практическое руководство. Программное перемещение листов в книгах](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Практическое руководство. Программный выбор листов Excel](../vsto/how-to-programmatically-select-worksheets.md)   
 [Практическое руководство. Программное добавление новых листов в книги Excel](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Ведущие элементы листа](../vsto/worksheet-host-item.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  