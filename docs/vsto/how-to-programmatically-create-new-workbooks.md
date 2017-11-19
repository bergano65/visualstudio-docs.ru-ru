---
title: "Как: программным путем создания новых книг | Документы Microsoft"
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
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
ms.assetid: be0196fe-7dc5-4811-b0cd-3c219731a3ff
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 59578b57bcff053558eba522e88c2e246fc45942
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Практическое руководство. Программное создание книг Excel
  При создании книги программными средствами она является собственным объектом <xref:Microsoft.Office.Interop.Excel.Workbook>, а не ведущим элементом <xref:Microsoft.Office.Tools.Excel.Workbook>.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 В проекте надстройки VSTO можно создать ведущий элемент <xref:Microsoft.Office.Tools.Excel.Workbook> для объекта <xref:Microsoft.Office.Interop.Excel.Workbook>. Дополнительные сведения см. в разделе [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-create-a-new-workbook"></a>Создание новой книги  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Workbooks>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]  
  
    > [!NOTE]  
    >  Книгу можно создать на основе шаблона, отличного от шаблона по умолчанию: для этого требуемый шаблон следует передать в качестве параметра в метод <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>.  
  
## <a name="see-also"></a>См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Работа с книгами](../vsto/working-with-workbooks.md)   
 [Как: открытие книг](../vsto/how-to-programmatically-open-workbooks.md)   
 [Как: программное Сохранение книг](../vsto/how-to-programmatically-save-workbooks.md)   
 [Как: программное закрытие книг Excel](../vsto/how-to-programmatically-close-workbooks.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)  
  
  