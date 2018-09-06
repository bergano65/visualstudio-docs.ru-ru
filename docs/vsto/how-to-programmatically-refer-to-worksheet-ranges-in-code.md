---
title: 'Практическое: ссылки на диапазоны листов в коде программными средствами'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 608ce006ccc34330631da8d4c947405b027f1a1f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674799"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Практическое: ссылки на диапазоны листов в коде программными средствами
  Подобный процесс используется для ссылки на содержимое <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления или собственный объект диапазона Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>Использование элемента управления NamedRange  
 В следующем примере добавляется <xref:Microsoft.Office.Tools.Excel.NamedRange> на лист и затем добавляет текст в ячейку в диапазоне.  
  
### <a name="to-refer-to-a-namedrange-control"></a>Для ссылки на элемент управления NamedRange  
  
1.  Назначить строке <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> свойство <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="use-native-excel-ranges"></a>Использование собственного диапазонах Excel  
 В следующем примере, добавляет собственный диапазон Excel на лист и затем добавляет текст в ячейку в диапазоне.  
  
### <a name="to-refer-to-a-native-range-object"></a>Для ссылки на собственный объект диапазона  
  
1.  Назначить строке <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> свойство диапазона.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Практическое: Программная проверка орфографии на листах](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Практическое: программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Практическое: программным образом автоматически заполнить диапазонов с постепенным изменением данных](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Практическое: программный поиск текста в диапазонах листа](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  