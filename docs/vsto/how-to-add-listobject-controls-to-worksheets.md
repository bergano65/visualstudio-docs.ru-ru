---
title: "Практическое руководство. Добавление элементов управления ListObject на листы | Microsoft Docs"
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
  - "элемент управления ListObject control, добавление в листы"
  - "элементы управления [разработка решений Office в Visual Studio], добавление в листы"
ms.assetid: 40788ecb-937f-4d2a-90ba-9c938e495b74
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Практическое руководство. Добавление элементов управления ListObject на листы
  Элементы управления <xref:Microsoft.Office.Tools.Excel.ListObject> можно добавлять в лист Microsoft Office Excel во время разработки и во время выполнения в проектах на уровне документа.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Элементы управления <xref:Microsoft.Office.Tools.Excel.ListObject> также можно добавлять во время выполнения в проектах надстроек VSTO.  
  
 В этом разделе описываются следующие задачи.  
  
-   [Добавление элементов управления ListObject во время разработки](#designtime)  
  
-   [Добавление элементов управления ListObject во время выполнения в проекте уровня документа](#runtimedoclevel)  
  
-   [Добавление элементов управления ListObject во время выполнения в проекте надстройки VSTO](#runtimeaddin)  
  
 Дополнительные сведения об элементах управления <xref:Microsoft.Office.Tools.Excel.ListObject> см. в разделе [Элемент управления ListObject](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a> Добавление элементов управления ListObject во время разработки  
 Существует несколько способов добавления элементов управления <xref:Microsoft.Office.Tools.Excel.ListObject> на лист в проекте уровня документа во время разработки: из Excel, из **панели элементов** Visual Studio и из окна **Источники данных**.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Использование ленты в Excel  
  
1.  На вкладке **Вставка** в группе **Таблицы** щелкните элемент **Таблица**.  
  
2.  Выделите ячейки, которые хотите включить в список, и нажмите кнопку **ОК**.  
  
#### Использование панели элементов  
  
1.  Из вкладки **Элементы управления Excel** на **панели элементов** перетащите <xref:Microsoft.Office.Tools.Excel.ListObject> в лист.  
  
     Откроется диалоговое окно **Добавление элемента управления ListObject**.  
  
2.  Выделите ячейки, которые хотите включить в список, и нажмите кнопку **ОК**.  
  
     Если вы не хотите использовать имя по умолчанию, измените его в окне **Свойства**.  
  
#### Использование окна "Источники данных".  
  
1.  Откройте окно **Источники данных** и создайте источник данных для проекта. Дополнительные сведения см. в разделе [Практическое руководство. Подключение к данным в базе данных](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md).  
  
2.  Перетащите таблицу из окна **Источники данных** в лист.  
  
     Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным добавится в лист. Для получения дополнительной информации см. [Связывание данных и Windows Forms](../Topic/Data%20Binding%20and%20Windows%20Forms.md).  
  
##  <a name="runtimedoclevel"></a> Добавление элементов управления ListObject во время выполнения в проекте уровня документа  
 Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> можно добавлять динамически во время выполнения. Это позволяет создавать элементы управления ведущего приложения при возникновении определенных событий. При закрытии листа динамически созданные объекты списка не сохраняются на листе как элементы управления ведущего приложения. Для получения дополнительной информации см. [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Добавление элемента управления ListObject в лист программными средствами  
  
1.  В обработчике событий <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> для `Sheet1` вставьте следующий код, чтобы добавить элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> в ячейки с **A1** до **A4**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Добавление элементов управления ListObject во время выполнения в проекте надстройки VSTO  
 Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> можно добавить программными средствами в любой открытый лист в проекте надстройки VSTO. При сохранении и закрытии листа динамически созданные объекты списка не сохраняются на листе как элементы управления ведущего приложения. Дополнительные сведения см. в разделе [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### Добавление элемента управления ListObject в лист программными средствами  
  
1.  Следующий код создает ведущий элемент листа, который основан на открытом листе, а затем добавляет элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> в ячейки с **A1** до **A4**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#8)]  
  
## См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Элемент управления ListObject](../vsto/listobject-control.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Практическое руководство. Изменение размера элементов управления ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  