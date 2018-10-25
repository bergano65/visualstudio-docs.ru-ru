---
title: 'Практическое: Добавление элементов управления NamedRange на листы'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 35febfa4c4d13b3f5d3d279f7d1c35e96051d54b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867121"
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Практическое: Добавление элементов управления NamedRange на листы
  Вы можете добавить <xref:Microsoft.Office.Tools.Excel.NamedRange> элементов управления на лист Microsoft Office Excel во время разработки и во время выполнения в проектах уровня документа.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Можно также добавить <xref:Microsoft.Office.Tools.Excel.NamedRange> элементов управления во время выполнения в проектах надстройки VSTO.  
  
 В этом разделе описываются следующие задачи.  
  
- [Добавление элементов управления NamedRange во время разработки](#designtime)  
  
- [Добавление элементов управления NamedRange во время выполнения в проекте уровня документа](#runtimedoclevel)  
  
- [Добавление элементов управления NamedRange во время выполнения в проекте надстройки VSTO](#runtimeaddin)  
  
  Дополнительные сведения о <xref:Microsoft.Office.Tools.Excel.NamedRange> элементов управления, см. в разделе [элемент управления NamedRange](../vsto/namedrange-control.md).  
  
##  <a name="designtime"></a> Добавление элементов управления NamedRange во время разработки  
 Существует несколько способов добавления элементов управления <xref:Microsoft.Office.Tools.Excel.NamedRange> на лист в проекте уровня документа во время разработки: из Excel, из **панели элементов**Visual Studio и из окна **Источники данных** .  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Добавление элемента управления NamedRange на лист с помощью поля "Имя" в Excel  
  
1.  Выделите ячейки, которые необходимо включить в именованный диапазон.  
  
2.  В **поле "имя"**, введите имя диапазона и нажмите клавишу **ввод**.  
  
     Поле **Имя** находится рядом со строкой формул над столбцом **A** листа.  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>Добавление на лист элемента управления NamedRange с помощью панели элементов  
  
1.  Откройте **панель элементов** и выберите вкладку **Элементы управления Excel** .  
  
2.  Перетащите элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> на лист.  
  
     Откроется диалоговое окно **Добавление именованного диапазона** .  
  
3.  Выделите ячейки, которые необходимо включить в именованный диапазон.  
  
4.  Нажмите кнопку **ОК**.  
  
     Если вы не хотите использовать имя элемента управления по умолчанию, измените его в окне **Свойства** .  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>Добавление на лист элемента управления NamedRange с помощью окна "Источники данных"  
  
1.  Откройте окно **Источники данных** и создайте источник данных для проекта. Дополнительные сведения см. в разделе [Добавление новых подключений](../data-tools/add-new-connections.md).  
  
2.  Перетащите одно поле из окна **Источники данных** на лист.  
  
     Элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с привязкой к данным добавится на лист. Дополнительные сведения см. в разделе [привязка данных и Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Добавление элементов управления NamedRange во время выполнения в проекте уровня документа  
 Вы можете добавить <xref:Microsoft.Office.Tools.Excel.NamedRange> лист элемента управления программными средствами во время выполнения. Это позволяет создавать элементы управления ведущего приложения при возникновении определенных событий. Динамически созданные именованные диапазоны не сохраняются как ведущие элементы управления на листе при его закрытии. Дополнительные сведения см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Добавление на лист элемента управления NamedRange программными средствами  
  
1.  В обработчик событий <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> листа `Sheet1`вставьте приведенный ниже код для добавления элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в ячейку **A1** и присвоения его свойству <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> значения `Hello world!`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> Добавление элементов управления NamedRange во время выполнения в проекте надстройки VSTO  
 Элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> можно добавить программным образом на любой открытый лист в проекте надстройки VSTO. Динамически созданные именованные диапазоны не сохраняются как ведущие элементы управления на листе при его закрытии. Дополнительные сведения см. в разделе [документов расширения Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Добавление на лист элемента управления NamedRange программными средствами  
  
1.  В примере кода ниже сначала на основе открытого листа создается ведущий элемент листа, а затем в ячейку <xref:Microsoft.Office.Tools.Excel.NamedRange> A1 **добавляется элемент управления** , а его свойству <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> присваивается значение `Hello world`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Практическое: изменение размера элементов управления NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  