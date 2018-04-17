---
title: 'Как: программным путем создания новых книг | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0ba2054258beb762a6b554a49b7a64a77f83dd7a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Практическое руководство. Программное создание книг Excel
  При создании книги программными средствами она является собственным объектом <xref:Microsoft.Office.Interop.Excel.Workbook>, а не ведущим элементом <xref:Microsoft.Office.Tools.Excel.Workbook>.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 В проекте надстройки VSTO можно создать ведущий элемент <xref:Microsoft.Office.Tools.Excel.Workbook> для объекта <xref:Microsoft.Office.Interop.Excel.Workbook>. Для получения дополнительной информации см. [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
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
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)  
  
  