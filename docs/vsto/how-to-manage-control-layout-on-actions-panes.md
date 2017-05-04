---
title: "Практическое руководство. Управление структурой элементов управления в панели действий | Microsoft Docs"
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
  - "панели действий [разработка решений Office в Visual Studio], структура элемента управления"
  - "элементы управления [разработка решений Office в Visual Studio], структура в панели действий"
  - "смарт-документы [разработка решений Office в Visual Studio], структура элемента управления"
ms.assetid: 857550d0-b9c0-4d2f-a947-dd955bcf2823
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# Практическое руководство. Управление структурой элементов управления в панели действий
  По умолчанию панель действий закрепляется справа от документа или листа; однако ее можно также закрепить слева, сверху или снизу.  При использовании многочисленных пользовательских элементов управления можно записать код, чтобы уложить в стопку пользовательские элементы управления в панели действий.  Дополнительные сведения см. в разделе [Общие сведения о панели действий](../vsto/actions-pane-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Порядок стопки элементов управления зависит от вертикального или горизонтального положения закрепленной панели действий.  
  
> [!NOTE]  
>  Если пользователь изменяет размер панели действий во время выполнения, можно создать настройку, чтобы размер элементов управления изменялся вместе с панелью действий.  Можно также использовать свойство <xref:System.Windows.Forms.Control.Anchor%2A> элемента управления Windows Forms, чтобы закрепить элементы управления в панели действий.  Дополнительные сведения см. в разделе [Практическое руководство. Привязка элементов управления в формах Windows Forms](../Topic/How%20to:%20Anchor%20Controls%20on%20Windows%20Forms.md).  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях.  Эти элементы определяются используемым выпуском Visual Studio и его параметрами.  Дополнительные сведения см. в разделе [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Настройка порядка стопки для элементов управления панели действий  
  
1.  Откройте проект уровня документа для Microsoft Office Word, содержащий панель действий с разными элементами управления или вложенные элементы управления панели действий.  Дополнительные сведения см. в разделе [Практическое руководство. Добавление области действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
2.  В **Обозревателе решений** щелкните правой кнопкой мыши файл **ThisDocument.cs** или **ThisDocument.vb**, а затем нажмите **Просмотреть код**.  
  
3.  В обработчике событий <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> панели действий убедитесь, чтобы ориентация панели действий была горизонтальной.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#30)]  
  
4.  При горизонтальной ориентации уложите элементы управления панели слева направо; в противном случае уложите их сверху вниз.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#31)]  
  
5.  В C\# необходимо добавлять обработчик событий для `ActionsPane` в обработчик событий <xref:Microsoft.Office.Tools.Word.Document.Startup>.  Дополнительные сведения о создании обработчиков событий см. в разделе [Практическое руководство. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#32)]  
  
6.  Запустите проект и убедитесь, что элементы управления панели действий уложены в стопку слева направо при панели действий, закрепленной сверху документа, или сверху вниз при панели действий, закрепленной с правой стороны документа.  
  
## Пример  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#29)]  
  
## Компиляция кода  
 Для этого примера необходимо следующее.  
  
-   проект уровня документа Word с панелью действий, содержащей разные пользовательские элементы управления или вложенные элементы управления панели действий.  
  
## См. также  
 [Общие сведения о панели действий](../vsto/actions-pane-overview.md)   
 [Практическое руководство. Добавление области действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Практическое руководство. Добавление области действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  