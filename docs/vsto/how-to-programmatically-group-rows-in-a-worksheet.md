---
title: Руководство. программное группирование строк на листе
description: Сведения о программной группировке одной или нескольких целых строк в Microsoft Excel с помощью элемента управления NamedRange или собственного объекта диапазона Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eaa0bbcc2c26a36e43e862cbe5a8f117c2a1fb26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885421"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Руководство. программное группирование строк на листе
  Можно сгруппировать одну или несколько строк целиком. Чтобы создать группу на листе, используйте <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления или собственный объект диапазона Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Использование элемента управления NamedRange
 При добавлении <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления в проект уровня документа во время разработки можно использовать элемент управления для программного создания группы. В следующем примере предполагается, что <xref:Microsoft.Office.Tools.Excel.NamedRange> на одном листе есть три элемента управления `data2001` : `data2002` , и `dataAll` . Каждый именованный диапазон ссылается на целую строку на листе.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Создание группы элементов управления NamedRange на листе

1. Сгруппируйте три именованных диапазона, вызвав <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> метод каждого диапазона. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > Чтобы разгруппировать строки, вызовите <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> метод.

## <a name="use-native-excel-ranges"></a>Использовать собственные диапазоны Excel
 В коде предполагается, что у вас есть три диапазона Excel с именами `data2001` , `data2002` и `dataAll` на листе.

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Создание группы диапазонов Excel на листе

1. Сгруппируйте три именованных диапазона, вызвав <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> метод каждого диапазона. В следующем примере предполагается, что <xref:Microsoft.Office.Interop.Excel.Range> на одном листе есть три элемента управления с именами `data2001` , `data2002` и `dataAll` . Каждый именованный диапазон ссылается на целую строку на листе.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > Чтобы разгруппировать строки, вызовите <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> метод.

## <a name="see-also"></a>См. также раздел
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Как добавить элементы управления NamedRange в листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
