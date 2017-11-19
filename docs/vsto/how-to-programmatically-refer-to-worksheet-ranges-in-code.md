---
title: "Как: ссылки на диапазоны листов в коде программными средствами | Документы Microsoft"
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
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
ms.assetid: 113633b8-426a-4d02-b6b8-d459d1f110ea
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fa76eff8719242d0fa3e059ad325dbdfb587f2bc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Практическое руководство. Ссылки на диапазоны листов в коде программными средствами
  Подобный процесс используется для ссылки на содержимое <xref:Microsoft.Office.Tools.Excel.NamedRange> управления или собственный объект диапазона Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>С помощью элемента управления NamedRange  
 В следующем примере добавляется <xref:Microsoft.Office.Tools.Excel.NamedRange> на лист и затем добавляет текст в ячейку в диапазоне.  
  
#### <a name="to-refer-to-a-namedrange-control"></a>Для ссылки на элемент управления NamedRange  
  
1.  Назначить строке <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> свойства <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="using-native-excel-ranges"></a>Использование собственных диапазонов Excel  
 В следующем примере добавляется собственный диапазон Excel на лист и затем добавляет текст в ячейку в диапазоне.  
  
#### <a name="to-refer-to-a-native-range-object"></a>Для ссылки на собственный объект диапазона  
  
1.  Назначить строке <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> диапазона.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Как: Программная проверка орфографии на листах](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Как: программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Как: программным образом автоматическое заполнение диапазонов с постепенным изменением данных](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Как: программный поиск текста в диапазонах листа](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  