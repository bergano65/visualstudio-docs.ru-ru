---
title: "Использование элементов управления Windows Forms в листах Excel"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "элементы управления [разработка решений Office в Visual Studio], Элементы управления Windows Forms"
  - "Excel [разработка решений Office в Visual Studio], элементы управления Windows Forms"
  - "Windows Forms - элементы управления [разработка решений Office в Visual Studio], Excel"
ms.assetid: bbda7461-0d69-4b56-8ba3-418d63ba49db
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Использование элементов управления Windows Forms в листах Excel
  Элементы управления Windows Forms можно добавлять в листы Microsoft Office Excel тем же способом, каким они добавляются в формы Windows.  Общие сведения о работе с элементами управления в документах см. в разделе [Общие сведения об использовании элементов управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Рекомендации по использованию элементов управления в Excel  
 В Excel существуют некоторые особенности.  
  
### Соответствие размера управляющего элемента размеру ячейки  
 Можно настроить элемент управления для автоматического изменения размера при изменении размера родительской ячейки.  Дополнительные сведения см. в разделе [Практическое руководство. Изменение размера внутри ячеек листа Excel](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### Добавление компонентов, совместно используемых всеми листами  
 Можно добавить компоненты, которые должны совместно использоваться всеми листами, например <xref:System.Data.DataSet>, в конструктор книги, а не в листы.  Компонент появится в области компонентов.  
  
### Формула для внедрения элементов управления  
 При выборе элемента управления в Excel в **строке формул** отображается текст **\=EMBED\("WinForms.Control.Host",""\)**.  Этот текст является обязательным и не подлежит удалению.  
  
## См. также  
 [Практическое руководство. Изменение размера внутри ячеек листа Excel](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Практическое руководство. Скрытие элементов управления на листах при печати](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Пошаговое руководство. Изменение форматирования листа с использованием элементов управления CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Пошаговое руководство. Отображение текста в текстовом поле рабочего листа с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Пошаговое руководство. Обновление диаграммы на листе с помощью переключателей](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  