---
title: 'Как: Управление структурой элементов управления в панели действий | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0831740c612e4e9d4eddd47a0648302e9460f060
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Практическое руководство. Управление структурой элементов управления в панели действий
  Панель действий закрепляется справа от документа или листа по умолчанию. его можно закрепить слева, сверху или снизу. Если вы используете несколько пользовательских элементов управления, можно написать код, чтобы правильно размещать пользовательские элементы управления в панели действий. Дополнительные сведения см. в разделе [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Порядка следования элементов управления зависит от того, закреплена ли панель действий вертикально или горизонтально.  
  
> [!NOTE]  
>  Если пользователь изменяет размер панели действий во время выполнения, можно задать элементы управления для изменения размера с панели «действия». Вы можете использовать свойство <xref:System.Windows.Forms.Control.Anchor%2A> элемента управления Windows Forms, чтобы закрепить элементы управления на панели действий. Дополнительные сведения см. в разделе [как: закрепить элементы управления в формах Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Для задания порядка следования элементы управления панели действий  
  
1.  Откройте проект уровня документа для Microsoft Office Word, содержащий панель действий с несколькими пользовательскими элементами управления или элементы управления панели вложенных действий. Дополнительные сведения см. в разделе [как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
2.  Щелкните правой кнопкой мыши **ThisDocument.cs** или **ThisDocument.vb** в **обозревателе решений** и нажмите кнопку **Просмотр кода**.  
  
3.  В <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> обработчик событий панели действий, проверьте, нельзя ли горизонтальная ориентация в панели действий.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]  
  
4.  При горизонтальной ориентации стека элементы управления панели слева направо; в противном случае стека их сверху.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]  
  
5.  В C# необходимо добавить обработчик событий для `ActionsPane` для <xref:Microsoft.Office.Tools.Word.Document.Startup> обработчика событий. Сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]  
  
6.  Запустите проект и убедитесь, что элементы управления панели действий располагаются слева направо, когда панель действий закрепляется в верхней части документа и элементы управления располагаются сверху вниз при закреплении области действия в правой части документа.  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   Элементы управления, содержащий несколько пользовательских элементов управления панели действий или области действия вложенного проекта на уровне документа Word.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о панели действий](../vsto/actions-pane-overview.md)   
 [Как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Пошаговое руководство: Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  