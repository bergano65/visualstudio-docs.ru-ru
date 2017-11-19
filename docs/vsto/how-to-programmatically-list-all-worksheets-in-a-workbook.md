---
title: "Как: программное перечисление всех листов в книге | Документы Microsoft"
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
- workbooks, listing worksheets
- worksheets, listing
ms.assetid: 38b63d1d-6047-44e8-b089-c576c6179e4a
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 78941e2f1c26b8d8a9a2a4e5ed02c6f4bae7dc0c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Практическое руководство. Программное перечисление всех листов в книге
  Класс <xref:Microsoft.Office.Interop.Excel.Workbook> предоставляет объект <xref:Microsoft.Office.Interop.Excel.Worksheets>. Этот объект содержит коллекцию всех объектов <xref:Microsoft.Office.Interop.Excel.Worksheet> в книге.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Составление списка существующих в книге листов в настройке уровня документа  
  
1.  Следует выполнить итерацию коллекции <xref:Microsoft.Office.Interop.Excel.Worksheets> и отправить имя каждого листа в смещение ячейки из элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#21)]  
  
### <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>Составление списка существующих в книге листов в надстройке VSTO  
  
1.  Следует выполнить итерацию коллекции <xref:Microsoft.Office.Interop.Excel.Worksheets> и отправить имя каждого листа в смещение ячейки из объекта <xref:Microsoft.Office.Interop.Excel.Range>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Как: программное добавление новых листов в книги Excel](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Как: программное перемещение листов в книгах](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  