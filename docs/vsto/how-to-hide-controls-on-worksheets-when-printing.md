---
title: "Практическое руководство. Скрытие элементов управления на листах при печати"
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
  - "элементы управления [разработка решений Office в Visual Studio], скрытие во время печати"
  - "печать [разработка решений Office в Visual Studio], скрытие элементов управления"
  - "печать [разработка решений Office в Visual Studio], листы"
  - "листы, скрытие элементов управления при печати"
ms.assetid: a637fe9a-9de1-4162-8ff6-fe28ccd62389
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Практическое руководство. Скрытие элементов управления на листах при печати
  При выводе на печать документа Microsoft Office Excel, который содержит элементы управления Windows Forms, эти элементы управления видимы на распечатанном листе.  Эти элементы управления можно скрыть.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Если скрываются элементы управления, которые отображают данные, например, <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, то данные, отображаемые этим элементом управления, не будут видимы на распечатанном листе.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях.  Эти элементы определяются используемым выпуском Visual Studio и его параметрами.  Дополнительные сведения см. в разделе [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Чтобы скрыть элементы управления при выводе листа на печать  
  
1.  Создайте или откройте проект Excel в Visual Studio и убедитесь в том, что лист **Sheet1** отображается в конструкторе.  Дополнительные сведения о создании проектов см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Перетащите со вкладки **Стандартные элементы управления** в **панели элементов** элемент управления <xref:Microsoft.Office.Tools.Excel.Controls.Button> в ячейку `Sheet1`.  
  
3.  В окне **Свойства** установите для свойства <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> значение **False**.  
  
## См. также  
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Общие сведения об использовании элементов управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Практическое руководство. Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Практическое руководство. Изменение размера внутри ячеек листа Excel](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  