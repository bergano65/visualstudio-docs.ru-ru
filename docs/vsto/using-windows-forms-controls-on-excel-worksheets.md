---
title: С помощью элементов управления Windows Forms в листах Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: abc3e08a867af9b04d7ce1da1449f108a099b238
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823423"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>С помощью элементов управления Windows Forms в листах Excel
  Можно добавить элементы управления Windows Forms в Microsoft Office Excel Workbooks таким же образом, как добавить элементы управления Windows Forms. Общие сведения о работе с элементами управления в документах, см. в разделе [элементы управления Windows Forms на общие сведения о документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Вопросы управления для Excel  
 Существуют некоторые рекомендации, относящиеся к Excel.  
  
### <a name="match-control-size-to-cell-size"></a>Соответствие размера элемента управления размеру ячейки  
 Вы можете задать автоматическое изменение размера элемента управления при изменении размера его родительской ячейки. Дополнительные сведения см. в разделе [Как Изменение размера элементов управления в ячейках листа Excel](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="add-components-that-are-shared-by-all-worksheets"></a>Добавление компонентов, совместно используемых всеми листами  
 Вы можете добавлять компоненты, которые будут совместно использоваться всеми листами, такие как <xref:System.Data.DataSet>, не в сами листы, а в конструктор книги. Такой компонент будет отображаться в области компонентов.  
  
### <a name="formula-for-embedding-controls"></a>Формула для внедрения элементов управления  
 При выборе элемента управления в Excel вы увидите **=EMBED("WinForms.Control.Host","")** в **строке формул**. Этот текст обязательный, его не следует удалять.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Изменение размера элементов управления внутри ячеек листа Excel](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Практическое руководство. Скрытие элементов управления на листах при печати](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Пошаговое руководство: Изменение форматирования листа с использованием элементов управления CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Пошаговое руководство: Отображаемый текст в текстовом поле на листе с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Пошаговое руководство: Обновление диаграммы на листе с помощью переключателей](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
