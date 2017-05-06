---
title: "Практическое руководство. Добавление элементов управления диаграммой на листы"
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
  - "Chart - элемент управления [разработка решений Office в Visual Studio], добавление к листам"
  - "элементы управления [разработка решений Office в Visual Studio], добавление к листам"
ms.assetid: f02568e7-5caa-45b4-aa2a-4f73b0565d4e
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Практическое руководство. Добавление элементов управления диаграммой на листы
  Элементы управления <xref:Microsoft.Office.Tools.Excel.Chart> можно добавлять на лист Microsoft Office Excel во время разработки и во время выполнения в настройках на уровне документа.  Элементы управления <xref:Microsoft.Office.Tools.Excel.Chart> также можно добавлять во время выполнения в надстройках VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 В этом разделе описываются следующие задачи.  
  
-   [Добавление элементов управления «Диаграмма» во время разработки](#designtime)  
  
-   [Добавление элементов управления «Диаграмма» во время выполнения в проекте на уровне документа](#runtimedoclevel)  
  
-   [Добавление элементов управления «Диаграмма» во время выполнения в проекте надстройки VSTO](#runtimeaddin)  
  
 Дополнительные сведения об элементах управления <xref:Microsoft.Office.Tools.Excel.Chart> см. в разделе [Элемент управления "диаграмма"](../vsto/chart-control.md).  
  
##  <a name="designtime"></a> Добавление элементов управления «Диаграмма» во время разработки  
 Для добавления элемента управления <xref:Microsoft.Office.Tools.Excel.Chart> на лист можно использовать ту же процедуру, что и для добавления диаграммы в приложении.  
  
> [!NOTE]  
>  Элемент управления <xref:Microsoft.Office.Tools.Excel.Chart> недоступен в окне **Панель элементов** или **Источники данных**.  
  
#### Добавление элемента управления ведущего приложения «Диаграмма» на лист в Excel  
  
1.  На вкладке **Вставка** в группе **Диаграммы** щелкните **Столбец**, затем категорию диаграммы и требуемый тип диаграммы.  
  
2.  В диалоговом окне **Вставить диаграмму** нажмите кнопку **ОК**.  
  
3.  На вкладке **Разработка** в группе **Данные** щелкните **Выбор данных**.  
  
4.  В диалоговом окне **Выбор источника данных** в области **Диаграмма** щелкните **диапазон данных** и сбросьте все параметры, выбранные по умолчанию.  
  
5.  На листе **Данные для диаграммы** выделите диапазон ячеек, содержащий данные для диаграммы \(ячейки с **A5** по **D8**\).  
  
6.  В диалоговом окне **Выбор источника данных** нажмите кнопку **ОК**.  
  
##  <a name="runtimedoclevel"></a> Добавление элементов управления «Диаграмма» во время выполнения в проекте на уровне документа  
 Элемент управления <xref:Microsoft.Office.Tools.Excel.Chart> можно добавлять динамически во время выполнения.  При закрытии документа динамически созданные диаграммы не сохраняются в документе как элементы управления ведущего приложения.  Дополнительные сведения см. в разделе [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Добавление элемента управления «Диаграмма» на лист программным образом  
  
1.  В обработчике событий <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> для `Sheet1` вставьте следующий код, чтобы добавить элемент управления <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> Добавление элементов управления «Диаграмма» во время выполнения в проекте надстройки VSTO  
 Элемент управления <xref:Microsoft.Office.Tools.Excel.Chart> можно добавить программным образом на любой открытый лист в проекте надстройки VSTO.  Дополнительные сведения см. в статье [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 При закрытии листа динамически созданные элементы управления «Диаграмма» не сохраняются в листе как элементы управления ведущего приложения.  Дополнительные сведения см. в разделе [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Добавление элемента управления «Диаграмма» на лист программным образом  
  
1.  Следующий код создает ведущий элемент листа, который основан на открытом листе, а затем добавляет элемент управления <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#9)]  
  
## Компиляция кода  
 В этом примере необходимо соблюдать следующие требования.  
  
-   Данные для диаграммы хранятся в диапазоне с A5 по D8 на листе.  
  
## См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Элемент управления "диаграмма"](../vsto/chart-control.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  