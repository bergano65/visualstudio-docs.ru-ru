---
title: "Как: программное отображение строки в ячейке листа | Документы Microsoft"
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
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
ms.assetid: b19870ad-e132-49fd-994e-0a91710fa4c9
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e297a2f6c1752053557dd7bcea5adab1c2184aa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Практическое руководство. Программное отображение строки в ячейке листа
  В этом примере показано, как программным способом отображения текста в ячейке. Для отображения текста в ячейке, используйте <xref:Microsoft.Office.Tools.Excel.NamedRange> управления или собственный объект диапазона Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>С помощью элемента управления NamedRange  
 В этом примере используется <xref:Microsoft.Office.Tools.Excel.NamedRange> управления с именем `message`. Необходимо добавить элемент управления для настройки уровня документа во время разработки. Следующий код следует разместить в классе листа, а не в `ThisWorkbook` класса.  
  
#### <a name="to-display-text-in-a-namedrange-control"></a>Для отображения текста в элементе управления NamedRange  
  
1.  Установите для параметра <xref:Microsoft.Office.Tools.Excel.NamedRange> управления **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]  
  
## <a name="using-a-native-excel-range"></a>С помощью собственного диапазона Excel  
 Следующий код создает новый диапазон программными средствами и присваивает ему значение.  
  
#### <a name="to-display-text-in-an-excel-range"></a>Для отображения текста в диапазоне Excel  
  
1.  Получить диапазон в ячейку **A1** на `Sheet1` и задайте значение **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Сбор данных с использованием формы Windows Forms](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Устранение неполадок решений Office](../vsto/troubleshooting-office-solutions.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  