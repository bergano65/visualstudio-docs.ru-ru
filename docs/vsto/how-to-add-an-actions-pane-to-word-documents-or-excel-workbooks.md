---
title: "Как: Добавление панели действий в документы Word или книги Excel | Документы Microsoft"
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
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d259442104cfbd6b072d0068ab5f2b4f182f027f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Практическое руководство. Добавление области действий в документы Word или книги Excel
  Чтобы добавить панель действий в документ Microsoft Office Word или книге Microsoft Excel, необходимо сначала создайте пользовательский элемент управления Windows Forms. Затем добавьте пользовательский элемент управления <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> свойство `ThisDocument.ActionsPane` поля (Word) или `ThisWorkbook.ActionsPane` поля (Excel) в своем проекте.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-the-user-control"></a>Создание пользовательского элемента управления  
 Ниже показано, как создать пользовательский элемент управления в слове или проекта Excel. Он также добавляет в пользовательский элемент управления, который записывает текст в документ или книгу, при нажатии кнопки.  
  
#### <a name="to-create-the-user-control"></a>Создание пользовательского элемента управления  
  
1.  Откройте проект уровня документа Word или Excel в Visual Studio.  
  
2.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
3.  В **Добавление нового элемента** выберите **управления панели действий**, назовите его **HelloControl**и нажмите кнопку **добавить**.  
  
    > [!NOTE]  
    >  Можно также добавить **пользовательский элемент управления** в проект. Классы, создаваемые **управления панели действий** и **пользовательский элемент управления** элементы функционально эквивалентны.  
  
4.  Из **Windows Forms** вкладке **элементов** перетащите **кнопку** управления на элемент управления.  
  
    > [!NOTE]  
    >  Если элемент управления не виден в конструкторе, дважды щелкните **HelloControl** в **обозревателе решений**.  
  
5.  Добавьте код для <xref:System.Windows.Forms.Control.Click> обработчика событий кнопки. В следующем примере показан код для документа Microsoft Office Word.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  В C# необходимо добавить обработчик событий для нажатия кнопки. Можно заменить этот код в `HelloControl` конструктор после вызова `IntializeComponent`.  
  
     Сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="adding-the-user-control-to-the-actions-pane"></a>Добавление пользовательского элемента управления на панель действий  
 Чтобы отобразить панель действий, добавьте пользовательский элемент управления <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> свойство `ThisDocument.ActionsPane` поля (Word) или `ThisWorkbook.ActionsPane` поля (Excel).  
  
#### <a name="to-add-the-user-control-to-the-actions-pane"></a>Чтобы добавить пользовательский элемент управления на панель действий  
  
1.  Добавьте следующий код в `ThisDocument` или `ThisWorkbook` класса в качестве объявления уровня класса (не добавляйте этот код в метод).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  Добавьте следующий код в `ThisDocument_Startup` обработчик событий `ThisDocument` класса или `ThisWorkbook_Startup` обработчик событий `ThisWorkbook` класса.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о панели действий](../vsto/actions-pane-overview.md)   
 [Пошаговое руководство: Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Как: Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  