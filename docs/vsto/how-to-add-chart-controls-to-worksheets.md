---
title: "Как: Добавление элементов управления диаграммой на листы | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: f02568e7-5caa-45b4-aa2a-4f73b0565d4e
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 53b30bb62e4c4f4146b1c43b6fe08f9683ba4867
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Практическое руководство. Добавление элементов управления диаграммой на листы
  Элементы управления <xref:Microsoft.Office.Tools.Excel.Chart> можно добавлять на лист Microsoft Office Excel во время разработки и во время выполнения в настройках на уровне документа. Элементы управления <xref:Microsoft.Office.Tools.Excel.Chart> также можно добавлять во время выполнения в надстройках VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 В этом разделе описываются следующие задачи.  
  
-   [Добавление элементов управления диаграммы во время разработки](#designtime)  
  
-   [Добавление элементов управления диаграммы во время выполнения в проекте уровня документа](#runtimedoclevel)  
  
-   [Добавление элементов управления диаграммы во время выполнения в проекте надстройки VSTO](#runtimeaddin)  
  
 Дополнительные сведения о <xref:Microsoft.Office.Tools.Excel.Chart> элементов управления, в разделе [элемент управления диаграммы](../vsto/chart-control.md).  
  
##  <a name="designtime"></a>Добавление элементов управления диаграммы во время разработки  
 Для добавления элемента управления <xref:Microsoft.Office.Tools.Excel.Chart> на лист можно использовать ту же процедуру, что и для добавления диаграммы в приложении.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.Chart> Управления не доступен из **элементов** или **источники данных** окна.  
  
#### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Добавление элемента управления ведущего приложения «Диаграмма» на лист в Excel  
  
1.  На **вставить** вкладку в **диаграммы** щелкните **столбца**, выберите категорию диаграммы и выберите тип диаграммы.  
  
2.  В **вставить диаграмму** диалоговое окно, нажмите кнопку **ОК**.  
  
3.  На **разработки** вкладке **данные** щелкните **Выбор данных**.  
  
4.  В **Выбор источника данных** диалоговое окно, щелкните в **диаграммы** **диапазон данных** и снимите все выборы по умолчанию.  
  
5.  В **данные для диаграммы** листа, выделите диапазон ячеек, содержащий данные для диаграммы (ячейки **A5** через **D8**).  
  
6.  В **Выбор источника данных** диалоговое окно, нажмите кнопку **ОК**.  
  
##  <a name="runtimedoclevel"></a>Добавление элементов управления диаграммы во время выполнения в проекте уровня документа  
 Элемент управления <xref:Microsoft.Office.Tools.Excel.Chart> можно добавлять динамически во время выполнения. При закрытии документа динамически созданные диаграммы не сохраняются в документе как элементы управления ведущего приложения. Для получения дополнительной информации см. [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Добавление элемента управления «Диаграмма» на лист программным образом  
  
1.  В обработчике событий <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> для `Sheet1` вставьте следующий код, чтобы добавить элемент управления <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a>Добавление элементов управления диаграммы во время выполнения в проекте надстройки VSTO  
 Элемент управления <xref:Microsoft.Office.Tools.Excel.Chart> можно добавить программным образом на любой открытый лист в проекте надстройки VSTO. Для получения дополнительной информации см. [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 При закрытии листа динамически созданные элементы управления «Диаграмма» не сохраняются в листе как элементы управления ведущего приложения. Для получения дополнительной информации см. [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Добавление элемента управления «Диаграмма» на лист программным образом  
  
1.  Следующий код создает ведущий элемент листа, который основан на открытом листе, а затем добавляет элемент управления <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 В этом примере необходимо соблюдать следующие требования.  
  
-   Данные для диаграммы хранятся в диапазоне с A5 по D8 на листе.  
  
## <a name="see-also"></a>См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Элемент управления диаграммы](../vsto/chart-control.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  