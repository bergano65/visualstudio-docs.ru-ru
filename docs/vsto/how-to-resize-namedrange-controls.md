---
title: "Практическое руководство. Изменения размера элементов управления &quot;NamedRange&quot;"
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
  - "элементы управления [разработка решений Office в Visual Studio], изменение размера"
  - "элемент управления NamedRange, изменение размера"
  - "диапазоны, изменение размеров в Excel"
ms.assetid: 7d6f0b2f-be46-49b7-9f38-b4c8849683f7
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Практическое руководство. Изменения размера элементов управления &quot;NamedRange&quot;
  Вы можете задать размер элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> при его добавлении в документ Microsoft Office Excel и при желании изменить его размер позже.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 В проекте уровня документа размер именованного диапазона можно изменить во время разработки или во время выполнения. Вы также можете изменять размеры именованных диапазонов в надстройках VSTO уровня приложения во время выполнения.  
  
 В этом разделе описываются следующие задачи.  
  
-   [Изменение размеров элементов управления NamedRange во время разработки](#designtime)  
  
-   [Изменение размеров элементов управления NamedRange во время выполнения в проекте на уровне документа](#runtimedoclevel)  
  
-   [Изменение размеров элементов управления NamedRange во время выполнения в проекте надстройки VSTO](#runtimeaddin)  
  
##  <a name="designtime"></a> Изменение размеров элементов управления NamedRange во время разработки  
 Вы можете изменить размер именованного диапазона, повторно задав размер в диалоговом окне **Присвоить имя**.  
  
#### Изменение размера именованного диапазона с помощью диалогового окна "Присвоить имя"  
  
1.  Щелкните элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> правой кнопкой мыши.  
  
2.  В контекстном меню выберите команду **Управление именованными диапазонами**.  
  
     Откроется диалоговое окно **Присвоить имя**.  
  
3.  Выберите именованный диапазон, который нужно изменить.  
  
4.  Снимите флажок **Ссылается на**.  
  
5.  Выберите ячейки, которые нужно использовать для определения размера именованного диапазона.  
  
6.  Нажмите кнопку **ОК**.  
  
##  <a name="runtimedoclevel"></a> Изменение размеров элементов управления NamedRange во время выполнения в проекте на уровне документа  
 Изменить размер именованного диапазона можно программным способом, используя свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A>.  
  
> [!NOTE]  
>  В окне **Свойства** свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> помечено как доступное только для чтения.  
  
#### Изменение размера именованного диапазона программными средствами  
  
1.  Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в ячейке **A1** листа `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#4)]  
  
2.  Измените размер именованного диапазона так, чтобы он включал ячейку **B1**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a> Изменение размеров элементов управления NamedRange во время выполнения в проекте надстройки VSTO  
 Размер элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> можно изменять во время выполнения на любом открытом листе. Подробнее о том, как добавить элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> на лист с помощью надстройки VSTO, см. в разделе [Практическое руководство. Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
#### Изменение размера именованного диапазона программными средствами  
  
1.  Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в ячейке **A1** листа `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#10)]  
  
2.  Измените размер именованного диапазона так, чтобы он включал ячейку **B1**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#11)]  
  
## См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Практическое руководство. Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Практическое руководство. Изменение размеров элементов управления Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Практическое руководство. Изменение размера элементов управления ListObject](../vsto/how-to-resize-listobject-controls.md)  
  
  