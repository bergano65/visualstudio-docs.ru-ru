---
title: "Как: программная сортировка данных на листах | Документы Microsoft"
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
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
ms.assetid: 2fbc6e63-02ea-4624-8d6f-bed60e06c61e
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b519dad9f2736b7c4451dd01964b3b16cac8ad2d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Практическое руководство. Программная сортировка данных на листах
  Вы можете сортировать данные, содержащиеся в списках и диапазонах листа во время выполнения. Следующий код сортирует диапазон из нескольких столбцов с именем `Fruits` по данным в первом столбце, а затем по данным во втором столбце.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="sorting-data-in-a-document-level-customization"></a>Сортировка данных в настройке на уровне документа  
  
#### <a name="to-sort-data-in-a-namedrange-control"></a>Сортировка данных в элементе управления NamedRange  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange>. В следующем примере на листе должен находиться элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `Fruits`. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
     [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]  
  
 Поместите следующий код в файл Sheet1.vb или Sheet1.cs для сортировки данных в элементе управления <xref:Microsoft.Office.Tools.Excel.ListObject>. В коде предполагается, что на листе с именем `Sheet1` есть элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с именем `fruitList`.  
  
#### <a name="to-sort-data-in-a-listobject-control"></a>Сортировка данных в элементе управления ListObject  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> свойства <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]  
  
## <a name="sorting-data-in-a-vsto-add-in"></a>Сортировка данных в надстройке VSTO  
  
#### <a name="to-sort-data-in-a-native-range"></a>Сортировка данных в собственном диапазоне  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> неуправляемого элемента управления <xref:Microsoft.Office.Interop.Excel.Range> Excel. В следующем примере на листе должен находиться неуправляемый элемент управления Excel с именем `Fruits`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]  
  
#### <a name="to-sort-data-in-a-listobject-control"></a>Сортировка данных в элементе управления ListObject  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> свойства <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> неуправляемого элемента управления <xref:Microsoft.Office.Interop.Excel.ListObject> Excel. В следующем примере предполагается, что на активном листе есть неуправляемый элемент управления <xref:Microsoft.Office.Interop.Excel.ListObject> Excel с именем `fruitList`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Как: программным образом автоматическое заполнение диапазонов с постепенным изменением данных](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Как: ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Как: программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Элемент управления ListObject](../vsto/listobject-control.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  