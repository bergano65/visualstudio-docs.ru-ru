---
title: 'Как: скрытие элементов управления на листах при печати | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4d02d823e707054fd17a5f3f892db41258b08081
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Практическое руководство. Скрытие элементов управления на листах при печати
  При печати документа Microsoft Office Excel, который содержит элементы управления Windows Forms, элементы управления видимы на распечатанном листе. Печать листа, можно скрыть элементы управления.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Если скрыть элементы управления, которые отображают данные, такие как <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, данные в элементе управления не видны на распечатанном листе.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Чтобы скрыть элементы управления, когда лист выводится на печать  
  
1.  Создайте или откройте проект Excel в Visual Studio и убедитесь, что **Sheet1** является видимым в конструкторе. Сведения о создании проектов см. в разделе [как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Из **стандартные элементы управления** вкладке **элементов**, перетащите <xref:Microsoft.Office.Tools.Excel.Controls.Button> управления в ячейку на `Sheet1`.  
  
3.  В **свойства** задайте <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> свойства **False**.  
  
## <a name="see-also"></a>См. также  
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Элементы управления в документах Office Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Как: Добавление элементов управления в документы Office Windows Forms](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Практическое руководство. Изменение размера элементов управления в ячейках листа Excel](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  