---
title: 'Как: программным образом автоматическое заполнение диапазонов с постепенным изменением данных | Документы Microsoft'
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
ms.openlocfilehash: e358869dea101d0c0ca012acd46b7822e6cf5873
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Практическое руководство. Автоматическое заполнение диапазонов данными, значения которых изменяются с постоянным шагом, с помощью программных средств
  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Метод <xref:Microsoft.Office.Interop.Excel.Range> позволяет также автоматического заполнения диапазона на листе значениями. Чаще всего <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> метод используется для хранения постепенно увеличения или уменьшения значения в диапазоне. Можно указать поведение, необязательную константу из <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> перечисления.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 При использовании двух диапазонов необходимо указать <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:  
  
-   Диапазон, который вызывает <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> метод, который указывает начальную точку заливки и содержит начальное значение.  
  
-   Диапазон, который требуется заполнить, переданный в качестве параметра для <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> метод. Целевой диапазон должен включать диапазон, содержащий исходное значение.  
  
    > [!NOTE]  
    >  Невозможно передать <xref:Microsoft.Office.Tools.Excel.NamedRange> управления вместо <xref:Microsoft.Office.Interop.Excel.Range>. Для получения дополнительной информации см. [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Первая ячейка диапазона, который требуется заполнить должна содержать начальное значение.  
  
 В этом примере предполагается, что заполнении трех регионах:  
  
-   Столбец B предназначен для хранения пяти дней недели. В качестве начального значения введите **понедельник** в ячейке B1.  
  
-   Столбец C предназначен для хранения пяти месяцев. В качестве начального значения введите **января** в ячейке C1.  
  
-   Столбец D предназначен для хранения ряда чисел, увеличивая на два для каждой строки. Начальные значения, введите **4** в ячейке D1 и **6** в ячейке D2.  
  
## <a name="see-also"></a>См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Как: ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Как: программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Как: программное выполнение вычислений Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  