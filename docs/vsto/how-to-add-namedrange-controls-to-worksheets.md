---
title: "Практическое руководство. Добавление элементов управления NamedRange на листы"
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
  - "диапазоны, добавление на листы"
  - "элемент управления NamedRange, добавление на листы"
  - "элементы управления [разработка решений Office в Visual Studio], добавление на листы"
ms.assetid: da7ec48f-92cb-4fa3-b3e2-447c238d17a8
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Практическое руководство. Добавление элементов управления NamedRange на листы
  Элементы управления <xref:Microsoft.Office.Tools.Excel.NamedRange> можно добавлять на лист Microsoft Office Excel во время разработки и во время выполнения в проектах на уровне документа.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Элементы управления <xref:Microsoft.Office.Tools.Excel.NamedRange> также можно добавлять во время выполнения в проектах надстроек VSTO.  
  
 В этом разделе описываются следующие задачи.  
  
-   [Добавление элементов управления NamedRange во время разработки.](#designtime)  
  
-   [Добавление элементов управления NamedRange во время выполнения в проекте на уровне документа.](#runtimedoclevel)  
  
-   [Добавление элементов управления NamedRange во время выполнения в проекте надстройки VSTO.](#runtimeaddin)  
  
 Дополнительные сведения об элементах управления <xref:Microsoft.Office.Tools.Excel.NamedRange> см. в разделе [Элемент управления NamedRange](../vsto/namedrange-control.md).  
  
##  <a name="designtime"></a> Добавление элементов управления NamedRange во время разработки  
 Существует несколько способов добавления элементов управления <xref:Microsoft.Office.Tools.Excel.NamedRange> на лист в проекте уровня документа во время разработки: из Excel, из **панели элементов** Visual Studio и из окна **Источники данных**.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Добавление элемента управления NamedRange на лист с помощью поля "Имя" в Excel  
  
1.  Выделите ячейки, которые необходимо включить в именованный диапазон.  
  
2.  В поле **Имя** введите имя диапазона и нажмите клавишу ВВОД.  
  
     Поле **Имя** находится рядом со строкой формул над столбцом **A** листа.  
  
#### Добавление на лист элемента управления NamedRange с помощью панели элементов  
  
1.  Откройте **панель элементов** и выберите вкладку **Элементы управления Excel**.  
  
2.  Перетащите элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> на лист.  
  
     Откроется диалоговое окно **Добавление именованного диапазона**.  
  
3.  Выделите ячейки, которые необходимо включить в именованный диапазон.  
  
4.  Нажмите кнопку **ОК**.  
  
     Если вы не хотите использовать имя элемента управления по умолчанию, измените его в окне **Свойства**.  
  
#### Добавление на лист элемента управления NamedRange с помощью окна "Источники данных"  
  
1.  Откройте окно **Источники данных** и создайте источник данных для проекта. Для получения дополнительной информации см. [Практическое руководство. Подключение к данным в базе данных](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
2.  Перетащите одно поле из окна **Источники данных** на лист.  
  
     Элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с привязкой к данным добавится на лист. Дополнительные сведения см. в разделе [Связывание данных и Windows Forms](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27).  
  
##  <a name="runtimedoclevel"></a> Добавление элементов управления NamedRange во время выполнения в проекте на уровне документа  
 Элементы управления <xref:Microsoft.Office.Tools.Excel.NamedRange> можно добавлять на лист программными средствами во время выполнения. Это позволяет создавать элементы управления ведущего приложения при возникновении определенных событий. Динамически созданные именованные диапазоны не сохраняются как ведущие элементы управления на листе при его закрытии. Дополнительные сведения см. в разделе [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Добавление на лист элемента управления NamedRange программными средствами  
  
1.  В обработчик событий <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> листа `Sheet1` вставьте приведенный ниже код для добавления элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в ячейку **A1** и присвоения его свойству <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> значения `Hello world!`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> Добавление элементов управления NamedRange во время выполнения в проекте надстройки VSTO  
 Элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> можно добавить программными средствами на любой открытый лист в проекте надстройки VSTO. Динамически созданные именованные диапазоны не сохраняются как ведущие элементы управления на листе при его закрытии. Для получения дополнительной информации см. [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### Добавление на лист элемента управления NamedRange программными средствами  
  
1.  В примере кода ниже сначала на основе открытого листа создается ведущий элемент листа, а затем в ячейку **A1** добавляется элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange>, а его свойству <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> присваивается значение `Hello world`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#7)]  
  
## См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Практическое руководство. Изменения размера элементов управления "NamedRange"](../vsto/how-to-resize-namedrange-controls.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  