---
title: Использование Windows Forms элементы управления на листах Excel | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: d4c754c0fff7f7a0f5c3bf31293696e3ec57961f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="using-windows-forms-controls-on-excel-worksheets"></a>Использование элементов управления Windows Forms в листах Excel
  Можно добавить элементы управления Windows Forms для книг Microsoft Office Excel таким же образом, как добавить элементы управления Windows Forms. Общие сведения о работе с элементами управления в документы см. в разделе [элементов управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Вопросы управления для Excel  
 Существуют некоторые особенности, которые относятся к Excel.  
  
### <a name="matching-control-size-to-cell-size"></a>Соответствие размера управляющего элемента размеру ячейки  
 Вы можете задать автоматическое изменение размера элемента управления при изменении размера его родительской ячейки. Дополнительные сведения см. в разделе [как: изменение размеров элементов управления внутри ячеек листа Excel](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="adding-components-that-are-shared-by-all-worksheets"></a>Добавление компонентов, совместно используемых всеми листами  
 Вы можете добавлять компоненты, которые будут совместно использоваться всеми листами, такие как <xref:System.Data.DataSet>, не в сами листы, а в конструктор книги. Такой компонент будет отображаться в области компонентов.  
  
### <a name="formula-for-embedding-controls"></a>Формула для внедрения элементов управления  
 При выборе элемента управления в Excel вы увидите **=EMBED("WinForms.Control.Host","")** в **строке формул**. Этот текст обязательный, его не следует удалять.  
  
## <a name="see-also"></a>См. также  
 [Как: изменение размера элементов управления внутри ячеек листа Excel](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Как: скрытие элементов управления на листах при печати](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Пошаговое руководство: Изменение форматирования листа с использованием элементов управления CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Пошаговое руководство: Отображение текста в текстовом поле на листе с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Пошаговое руководство. Обновление диаграммы на листе с помощью переключателей](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  