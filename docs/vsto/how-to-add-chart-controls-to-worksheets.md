---
title: 'Практическое: Добавление элементов управления диаграммой на листы'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 713657c7df5bfd3dd3f864c15ffc86dd1d531eac
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919927"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Практическое: Добавление элементов управления диаграммой на листы
  Вы можете добавить <xref:Microsoft.Office.Tools.Excel.Chart> элементов управления на лист Microsoft Office Excel во время разработки и во время выполнения в настройках уровня документа. Можно также добавить <xref:Microsoft.Office.Tools.Excel.Chart> элементов управления во время выполнения в надстройках VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 В этом разделе описываются следующие задачи.  
  
- [Добавить элементы управления диаграммы во время разработки](#designtime)  
  
- [Добавить элементы управления диаграммы во время выполнения в проекте уровня документа](#runtimedoclevel)  
  
- [Добавить элементы управления диаграммы во время выполнения в проекте надстройки VSTO](#runtimeaddin)  
  
  Дополнительные сведения о <xref:Microsoft.Office.Tools.Excel.Chart> элементов управления, см. в разделе [диаграммы управления](../vsto/chart-control.md).  
  
##  <a name="designtime"></a> Добавить элементы управления диаграммы во время разработки  
 Для добавления элемента управления <xref:Microsoft.Office.Tools.Excel.Chart> на лист можно использовать ту же процедуру, что и для добавления диаграммы в приложении.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.Chart> Управления не доступен из **элементов** или **источников данных** окна.  
  
### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Добавление элемента управления ведущего приложения «Диаграмма» на лист в Excel  
  
1.  На **вставить** на вкладке **диаграммы** щелкните **столбец**, затем категорию диаграммы и выберите тип диаграммы.  
  
2.  В **вставить диаграмму** диалоговом окне щелкните **ОК**.  
  
3.  На **разработки** на вкладке **данных** щелкните **Выбор данных**.  
  
4.  В **Выбор источника данных** диалоговое окно, щелкните в **диаграммы** **диапазон данных** и снимите все выборы по умолчанию.  
  
5.  В **данные для диаграммы** листа, выделите диапазон ячеек, содержащий данные для диаграммы (ячейки **A5** через **D8**).  
  
6.  В **Выбор источника данных** диалоговом окне щелкните **ОК**.  
  
##  <a name="runtimedoclevel"></a> Добавить элементы управления диаграммы во время выполнения в проекте уровня документа  
 Вы можете добавить <xref:Microsoft.Office.Tools.Excel.Chart> управления динамически во время выполнения. При закрытии документа динамически созданные диаграммы не сохраняются в документе как элементы управления ведущего приложения. Дополнительные сведения см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Добавление элемента управления «Диаграмма» на лист программным образом  
  
1.  В обработчике событий <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> для `Sheet1` вставьте следующий код, чтобы добавить элемент управления <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> Добавить элементы управления диаграммы во время выполнения в проекте надстройки VSTO  
 Элемент управления <xref:Microsoft.Office.Tools.Excel.Chart> можно добавить программным образом на любой открытый лист в проекте надстройки VSTO. Дополнительные сведения см. в разделе [документов расширения Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 При закрытии листа динамически созданные элементы управления «Диаграмма» не сохраняются в листе как элементы управления ведущего приложения. Дополнительные сведения см. в разделе [Add Controls to Office документов во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Добавление элемента управления «Диаграмма» на лист программным образом  
  
1.  Следующий код создает ведущий элемент листа, который основан на открытом листе, а затем добавляет элемент управления <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 В этом примере необходимо соблюдать следующие требования.  
  
-   Данные для диаграммы хранятся в диапазоне с A5 по D8 на листе.  
  
## <a name="see-also"></a>См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Элемент управления диаграммы](../vsto/chart-control.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  