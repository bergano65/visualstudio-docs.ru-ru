---
title: 'Практическое: изменение размера элементов управления NamedRange'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6d785aba9d08f71aa8530bc2edd015f497caafef
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673938"
---
# <a name="how-to-resize-namedrange-controls"></a>Практическое: изменение размера элементов управления NamedRange
  Вы можете задать размер элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> при его добавлении в документ Microsoft Office Excel и при желании изменить его размер позже.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 В проекте уровня документа размер именованного диапазона можно изменить во время разработки или во время выполнения. Вы также можете изменять размеры именованных диапазонов в надстройках VSTO уровня приложения во время выполнения.  
  
 В этом разделе описываются следующие задачи.  
  
-   [Изменение размера элементов управления NamedRange во время разработки](#designtime)  
  
-   [Изменение размера элементов управления NamedRange во время выполнения в проекте уровня документа](#runtimedoclevel)  
  
-   [Изменение размера элементов управления NamedRange во время выполнения в проекте надстройки VSTO](#runtimeaddin)  
  
##  <a name="designtime"></a> Изменение размера элементов управления NamedRange во время разработки  
 Вы можете изменить размер именованного диапазона, повторно задав размер в диалоговом окне **Присвоить имя** .  
  
### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Изменение размера именованного диапазона с помощью диалогового окна "Присвоить имя"  
  
1.  Щелкните элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> правой кнопкой мыши.  
  
2.  В контекстном меню выберите команду **Управление именованными диапазонами** .  
  
     Откроется диалоговое окно **Присвоить имя** .  
  
3.  Выберите именованный диапазон, который нужно изменить.  
  
4.  Снимите флажок **Ссылается на** .  
  
5.  Выберите ячейки, которые нужно использовать для определения размера именованного диапазона.  
  
6.  Нажмите кнопку **ОК**.  
  
##  <a name="runtimedoclevel"></a> Изменение размера элементов управления NamedRange во время выполнения в проекте уровня документа  
 Изменить размер именованного диапазона можно программным способом, используя свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> .  
  
> [!NOTE]  
>  В окне **Свойства** свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> помечено как доступное только для чтения.  
  
### <a name="to-resize-a-named-range-programmatically"></a>Изменение размера именованного диапазона программными средствами  
  
1.  Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в ячейке **A1** листа `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]  
  
2.  Измените размер именованного диапазона так, чтобы он включал ячейку **B1**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a> Изменение размера элементов управления NamedRange во время выполнения в проекте надстройки VSTO  
 Вы можете изменить размер <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления в любой открытый лист во время выполнения. Дополнительные сведения о добавлении <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления на лист с помощью надстройки VSTO, см. в разделе [как: элементов управления NamedRange, добавление на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
### <a name="to-resize-a-named-range-programmatically"></a>Изменение размера именованного диапазона программными средствами  
  
1.  Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в ячейке **A1** листа `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]  
  
2.  Измените размер именованного диапазона так, чтобы он включал ячейку **B1**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]  
  
## <a name="see-also"></a>См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Практическое: Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Практическое: изменение размера элементов управления Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Практическое: изменение размера элементов управления ListObject](../vsto/how-to-resize-listobject-controls.md)  
  
  