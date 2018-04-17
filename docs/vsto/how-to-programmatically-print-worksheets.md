---
title: 'Как: программная печать листов | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d9bd4d28afb1eca2ff07a8847081864c7af5744
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-print-worksheets"></a>Практическое руководство. Программная печать листов Excel
  Любой лист в книге можно напечатать.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="printing-a-worksheet-in-a-document-level-customization"></a>Печать листа в настройке на уровне документа  
  
#### <a name="to-print-a-worksheet"></a>Печать листа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> `Sheet1`, запросите две копии и просмотрите документ перед печатью.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]  
  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> Метод позволяет отобразить указанный объект в **предварительного просмотра перед печатью** окна. В следующем коде предполагается, что существует ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> с именем `Sheet1`.  
  
#### <a name="to-preview-a-page-before-printing"></a>Предварительный просмотр страницы перед печатью  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> листа.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]  
  
## <a name="printing-a-worksheet-in-a-vsto-add-in"></a>Печать листа в надстройке VSTO  
  
#### <a name="to-print-a-worksheet"></a>Печать листа  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> активного листа, запросите две копи и просмотрите документ перед печатью.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]  
  
 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> Метод позволяет отобразить указанный объект в **предварительного просмотра перед печатью** окна.  
  
#### <a name="to-preview-a-page-before-printing"></a>Предварительный просмотр страницы перед печатью  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> активного листа.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Как: Программная проверка орфографии на листах](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Ведущие элементы листа](../vsto/worksheet-host-item.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  