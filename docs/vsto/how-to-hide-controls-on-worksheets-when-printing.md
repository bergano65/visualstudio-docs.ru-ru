---
title: 'Практическое: скрытие элементов управления на листах при печати'
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
ms.openlocfilehash: e240f4b4be5ce4092705615f060f4e0ef0076e3a
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254482"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Практическое: скрытие элементов управления на листах при печати
  При печати документа Microsoft Office Excel, который содержит элементы управления Windows Forms, элементы управления, отображаются при печати рабочего листа. Печать листа, можно скрыть элементы управления.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Если скрыть элементы управления, которые отображают данные, такие как <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, данные в элементе управления не видны на печати рабочего листа.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Чтобы скрыть элементы управления, когда лист печатается  
  
1.  Создайте или откройте проект Excel в Visual Studio и убедитесь, что **Sheet1** является видимым в конструкторе. Сведения о создании проектов см. в разделе [как: проектов Office, создайте в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Из **стандартные элементы управления** вкладке **элементов**, перетащите <xref:Microsoft.Office.Tools.Excel.Controls.Button> управления в ячейке на `Sheet1`.  
  
3.  В **свойства** окне <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> свойства **False**.  
  
## <a name="see-also"></a>См. также  
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Элементы управления Windows Forms на общие сведения о документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Практическое: Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Практическое: изменение размера элементов управления внутри ячеек листа Excel](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  