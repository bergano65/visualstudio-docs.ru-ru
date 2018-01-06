---
title: "Как: заполнение данными элементов управления ListObject | Документы Microsoft"
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
- disconnecting from data sources
- ListObject control, disconnecting from a data source
- ListObject control, filling with data
- data [Office development in Visual Studio], adding to worksheets
- data binding, ListObject controls
- worksheets, populating with data
ms.assetid: bf692c77-f5cc-456a-9a5c-84ed3067d7eb
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 93527f48c09a14d35ef88adf65b43272be71212c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-listobject-controls-with-data"></a>Практическое руководство. Заполнение данными элементов управления ListObject
  Вы можете использовать привязку данных как способ быстрого добавления данных в документ. После привязки данных к объекту-списку можно отключить этот объект-список, чтобы он отображал данные, но не был привязан к источнику данных.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [практические советы. Создание списка в Excel, подключенного к списку SharePoint?](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
### <a name="to-bind-data-to-a-listobject-control"></a>Привязка данных к элементу управления ListObject  
  
1.  Создайте <xref:System.Data.DataTable> на уровне класса.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#20)]  
  
2.  Добавьте примеры столбцов и данных в обработчик событий `Startup` класса `Sheet1` (в проекте уровня документа) или класса `ThisAddIn` (в проекте уровня приложения).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#21)]  
  
3.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> и передайте в него имена столбцов в порядке их отображения. Порядок столбцов в объекте-списке может отличаться от порядка, в котором они появляются в <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#22)]  
  
### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>Отключение элемента управления ListObject от источника данных  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> типа `List1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#23)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 В этом примере кода предполагается, что в листе, в котором этот код появляется, имеется существующий элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с именем `list1` .  
  
## <a name="see-also"></a>См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Как: сопоставление столбцов ListObject данным](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Элемент управления ListObject](../vsto/listobject-control.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Как: заполнение листов данными из базы данных](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Практическое руководство. Заполнение документов данными из служб](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  