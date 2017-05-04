---
title: "Практическое руководство. Программное копирование листов Excel | Microsoft Docs"
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
  - "Excel [разработка решений Office в Visual Studio], копирование листов"
  - "листы, копирование"
ms.assetid: e49e03f5-7b2f-416b-b5fe-0965336c47e1
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Практическое руководство. Программное копирование листов Excel
  Можно создать копию листа и вставить данный лист перед существующим листом в книге или после него.  Если место вставки листа не указано, Excel создает новую книгу, которая будет содержать новый лист.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Независимо от того, копируете ли вы лист программно или конечный пользователь копирует его вручную, код под новым листом отсутствует, а элементы управления на новом листе не работают.  Это происходит потому, что новый скопированный лист является объектом <xref:Microsoft.Office.Interop.Excel.Worksheet>, а не ведущим элементом <xref:Microsoft.Office.Tools.Excel.Worksheet>.  Элементы управления Windows Forms и элементы управления ведущего приложения можно добавлять только к ведущим элементам.  Дополнительные сведения см. в разделе [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### Добавление скопированного листа в книгу в настройке на уровне документа  
  
1.  Для копирования первого листа в текущей книге и размещения копии после третьего листа используйте метод <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#16)]  
  
### Добавление скопированного листа к книге в надстройке VSTO  
  
1.  Для копирования первого листа в текущей книге и размещения копии после третьего листа используйте метод <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Практическое руководство. Программное добавление новых листов в книги Excel](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Практическое руководство. Программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Практическое руководство. Программный выбор листов Excel](../vsto/how-to-programmatically-select-worksheets.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  