---
title: "Как: программная группировка строк на листе | Документы Microsoft"
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
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
ms.assetid: 48037dca-35a2-4df2-918b-6a9f568fae91
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f17c90fb5f10dfdc0658f9176e0e15cedcc6f1d5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Практическое руководство. Программная группировка строк на листах
  Можно группировать одного или нескольких полных строк. Чтобы создать группу на листе, используйте <xref:Microsoft.Office.Tools.Excel.NamedRange> управления или собственный объект диапазона Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>С помощью элемента управления NamedRange  
 При добавлении <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления в проекте уровня документа во время разработки, можно использовать элемент управления программным образом создать группу. В следующем примере предполагается, что имеются три <xref:Microsoft.Office.Tools.Excel.NamedRange> элементов управления на том же листе: `data2001`, `data2002`, и `dataAll`. Каждый именованный диапазон относится к целой строки на листе.  
  
#### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Создание группы элементов управления NamedRange на листе  
  
1.  Сгруппировать три именованных диапазонов, вызвав <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> метод для каждого диапазона. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Разгруппирование строк, вызвать <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> метод.  
  
## <a name="using-native-excel-ranges"></a>Использование собственных диапазонов Excel  
 В коде предполагается, что имеется три диапазона Excel с именем `data2001`, `data2002`, и `dataAll` на листе.  
  
#### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Создание группы диапазонов Excel на листе  
  
1.  Сгруппировать три именованных диапазонов, вызвав <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> метод для каждого диапазона. В следующем примере предполагается, что имеются три <xref:Microsoft.Office.Interop.Excel.Range> элементов управления с именем `data2001`, `data2002`, и `dataAll` на одном листе. Каждый именованный диапазон относится к целой строки на листе.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Разгруппирование строк, вызвать <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> метод.  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Как: Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  