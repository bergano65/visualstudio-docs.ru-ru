---
title: Как выполнить Программное отображение строки в ячейке листа
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d97e57f35298a14da5c4098b464f8248b93a0592
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871810"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Как выполнить Программное отображение строки в ячейке листа
  В этом примере показано, как для отображения текста в ячейке программными средствами. Для отображения текста в ячейке, используйте <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления или собственный объект диапазона Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>Использование элемента управления NamedRange  
 В этом примере используется <xref:Microsoft.Office.Tools.Excel.NamedRange> управления с именем `message`. Элемент управления необходимо добавить в настройку уровня документа во время разработки. Следующий код должен быть помещен в классе листа, не в `ThisWorkbook` класса.  
  
### <a name="to-display-text-in-a-namedrange-control"></a>Для отображения текста в элементе управления NamedRange  
  
1.  Установите для параметра <xref:Microsoft.Office.Tools.Excel.NamedRange> управления **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]  
  
## <a name="use-a-native-excel-range"></a>Используйте собственный диапазон Excel  
 Следующий код создает новый диапазон программным образом и присваивает ему значение.  
  
### <a name="to-display-text-in-an-excel-range"></a>Для отображения текста в диапазон Excel  
  
1.  Получить диапазон в ячейку **A1** на `Sheet1` и задайте значение **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Сбор данных с использованием формы Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Устранение неполадок решений Office](../vsto/troubleshooting-office-solutions.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
