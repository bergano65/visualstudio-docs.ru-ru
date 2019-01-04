---
title: Как выполнить Программное копирование листов Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a123191afe2a6aef18e9a4bc64f5bc966db6c479
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871308"
---
# <a name="how-to-programmatically-copy-worksheets"></a>Как выполнить Программное копирование листов Excel
  Можно создать копию листа и вставить данный лист перед существующим листом в книге или после него. Если место вставки листа не указано, Excel создает новую книгу, которая будет содержать новый лист.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Независимо от того, копируете ли вы лист программно или конечный пользователь копирует его вручную, код под новым листом отсутствует, а элементы управления на новом листе не работают. Это происходит потому, что новый скопированный лист является объектом <xref:Microsoft.Office.Interop.Excel.Worksheet>, а не ведущим элементом <xref:Microsoft.Office.Tools.Excel.Worksheet>. Элементы управления Windows Forms и элементы управления ведущего приложения можно добавлять только к ведущим элементам. Дополнительные сведения см. в разделе [программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Добавление скопированного листа в книгу в настройке на уровне документа  
  
1.  Для копирования первого листа в текущей книге и размещения копии после третьего листа используйте метод <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]  
  
## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Добавление скопированного листа к книге в надстройке VSTO  
  
1.  Для копирования первого листа в текущей книге и размещения копии после третьего листа используйте метод <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Практическое руководство. Программное добавление новых листов в книги](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Практическое руководство. Программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Практическое руководство. Программный выбор листов Excel](../vsto/how-to-programmatically-select-worksheets.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
