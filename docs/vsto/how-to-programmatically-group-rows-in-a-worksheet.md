---
title: Практическое руководство. Программная группировка строк на листах
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 269ecdb67fe58a5ad2aff6af63ba6ea45647811a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412622"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Практическое руководство. Программная группировка строк на листах
  Вы можете сгруппировать один или несколько целых строк. Чтобы создать группу на листе, используйте <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления или собственный объект диапазона Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Использование элемента управления NamedRange
 Если вы добавите <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления в проекте уровня документа во время разработки, можно использовать элемент управления программными средствами создать группу. В следующем примере предполагается, что существует три <xref:Microsoft.Office.Tools.Excel.NamedRange> элементов управления в том же листе: `data2001`, `data2002`, и `dataAll`. Каждый именованный диапазон относится к целой строке на листе.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Чтобы создать группу элементов управления NamedRange на лист

1. Сгруппировать три именованных диапазонов, вызвав <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> метод каждого диапазона. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > Разгруппирование строк, вызвать <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> метод.

## <a name="use-native-excel-ranges"></a>Использование собственного диапазонах Excel
 В коде предполагается, что у вас есть три диапазона Excel с именем `data2001`, `data2002`, и `dataAll` на рабочем листе.

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Чтобы создать группу диапазонов Excel на листе

1. Сгруппировать три именованных диапазонов, вызвав <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> метод каждого диапазона. В следующем примере предполагается, что существует три <xref:Microsoft.Office.Interop.Excel.Range> элементов управления с именем `data2001`, `data2002`, и `dataAll` на одном листе. Каждый именованный диапазон относится к целой строке на листе.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > Разгруппирование строк, вызвать <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> метод.

## <a name="see-also"></a>См. также
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Практическое руководство. Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
