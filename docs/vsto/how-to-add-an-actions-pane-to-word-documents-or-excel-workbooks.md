---
title: 'Практическое: Добавление панели действий в документы Word или книги Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f70511d0490032204789dc037a13847a10b5cbe6
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948365"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Практическое руководство. Добавление области действий в документы Word или книги Excel
  Чтобы добавить панели действий в документ Microsoft Office Word или книге Microsoft Excel, необходимо сначала создайте пользовательский элемент управления Windows Forms. Затем добавьте пользовательский элемент управления <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> свойство `ThisDocument.ActionsPane` поле (Word) или `ThisWorkbook.ActionsPane` поле (Excel) в проекте.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-the-user-control"></a>Создание пользовательского элемента управления  
 Ниже показано, как создать пользовательский элемент управления в Word или Excel проекта. Он также добавляет в пользовательский элемент управления, который записывает текст в документ или книгу, при нажатии кнопки.  
  
#### <a name="to-create-the-user-control"></a>Создание пользовательского элемента управления  
  
1.  Откройте проект уровня документа Word или Excel в Visual Studio.  
  
2.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
3.  В **Добавление нового элемента** выберите **элемента управления панели действий**, назовите его **HelloControl**и нажмите кнопку **добавить**.  
  
    > [!NOTE]  
    >  Можно также добавить **пользовательский элемент управления** в проект. Классы, создаваемые **элемента управления панели действий** и **пользовательский элемент управления** элементов функционально эквивалентны.  
  
4.  Из **Windows Forms** вкладке **элементов** перетащите **кнопку** управления на элемент управления.  
  
    > [!NOTE]  
    >  Если элемент управления не отображается в конструкторе, дважды щелкните **HelloControl** в **обозревателе решений**.  
  
5.  Добавьте код, чтобы <xref:System.Windows.Forms.Control.Click> обработчик событий кнопки. В следующем примере показан код для документа Microsoft Office Word.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  В C# необходимо добавить обработчик событий для нажатия кнопки. Можно поместить этот код в `HelloControl` конструктора после вызова `InitializeComponent`.  
  
     Сведения о том, как создавать обработчики событий, см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="add-the-user-control-to-the-actions-pane"></a>Добавление пользовательского элемента управления на панель действий  
 Чтобы отобразить панель действий, добавьте пользовательский элемент управления для <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> свойство `ThisDocument.ActionsPane` поле (Word) или `ThisWorkbook.ActionsPane` поле (Excel).  
  
### <a name="to-add-the-user-control-to-the-actions-pane"></a>Чтобы добавить пользовательский элемент управления на панель действий  
  
1.  Добавьте следующий код, чтобы `ThisDocument` или `ThisWorkbook` класс как объявление уровня класса (не добавляйте этот код в метод).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  Добавьте следующий код, чтобы `ThisDocument_Startup` обработчик событий `ThisDocument` класса или `ThisWorkbook_Startup` обработчик событий `ThisWorkbook` класса.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о панели действий](../vsto/actions-pane-overview.md)   
 [Пошаговое руководство: Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Практическое: Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Пошаговое руководство: Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  