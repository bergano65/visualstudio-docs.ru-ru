---
title: 'Как: открытие книг | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a243e4972bcee77aa9d76957ab5cce289e30e120
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-open-workbooks"></a>Практическое руководство. Программное открытие книг Excel
  <xref:Microsoft.Office.Interop.Excel.Workbooks> Коллекции в Microsoft Office Excel позволяет работать со всеми открытыми книгами и открывать книги.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-open-an-existing-workbook"></a>Чтобы открыть книгу  
  
1.  Используйте <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> метод <xref:Microsoft.Office.Interop.Excel.Workbooks> коллекции, передается путь к книге.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера кода требуется следующее.  
  
-   Книга с именем `YourWorkbook.xls` должен существовать в каталоге с именем `Test` на диске C.  
  
## <a name="see-also"></a>См. также  
 [Работа с книгами](../vsto/working-with-workbooks.md)   
 [Как: открытие текстовых файлов как книг](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Как: программным путем создания новых книг](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Как: программное Сохранение книг](../vsto/how-to-programmatically-save-workbooks.md)   
 [Как: программное закрытие книг Excel](../vsto/how-to-programmatically-close-workbooks.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)  
  
  