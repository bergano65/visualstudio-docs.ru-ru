---
title: 'Практическое: программным образом автоматически заполнить диапазонов с постепенным изменением данных'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a4fff7eb59ff2fe5e17ddf500bf546502492634d
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256407"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Практическое: программным образом автоматически заполнить диапазонов с постепенным изменением данных
  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Метод <xref:Microsoft.Office.Interop.Excel.Range> позволяет также автоматического заполнения диапазона на листе значениями. Чаще всего <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> метод используется для хранения постепенно увеличения или уменьшения значения в диапазоне. Можно указать поведение, необязательную константу из <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> перечисления.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 При использовании необходимо указать два диапазона <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:  
  
-   Диапазон, который вызывает <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> метод, который указывает начальную точку заливки и содержит начальное значение.  
  
-   Диапазон, который требуется заполнить, переданный в качестве параметра <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> метод. Целевой диапазон должен включать диапазон, содержащий исходное значение.  
  
    > [!NOTE]  
    >  Невозможно передать <xref:Microsoft.Office.Tools.Excel.NamedRange> управления вместо <xref:Microsoft.Office.Interop.Excel.Range>. Дополнительные сведения см. в разделе [программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Может содержать начальное значение первой ячейки диапазона, который требуется заполнить.  
  
 В примере вам понадобится ввести три области:  
  
-   Столбец B предназначен для хранения пяти дней недели. Начальное значение, введите **понедельник** в ячейке В1.  
  
-   Столбец C является включение пять месяцев. Начальное значение, введите **января** в ячейке C1.  
  
-   Столбец D является включение ряд чисел, увеличивая время на два для каждой строки. Начальные значения, введите **4** в ячейке D1 и **6** в ячейке D2.  
  
## <a name="see-also"></a>См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Практическое: ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Практическое: программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Практическое: программное выполнение вычислений Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  