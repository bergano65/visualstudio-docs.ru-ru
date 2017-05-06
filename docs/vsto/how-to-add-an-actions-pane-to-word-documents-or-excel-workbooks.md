---
title: "Практическое руководство. Добавление области действий в документы Word или книги Excel"
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
  - "панели действий [разработка решений Office в Visual Studio], добавление элементов управления"
  - "панели действий [разработка решений Office в Visual Studio], создание в Word"
  - "смарт-документы [разработка решений Office в Visual Studio], добавление элементов управления"
  - "смарт-документы [разработка решений Office в Visual Studio], создание в Word"
ms.assetid: cea3c2b6-9364-4134-b812-50888ad8bd76
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Практическое руководство. Добавление области действий в документы Word или книги Excel
  Добавление панели действий к документу слова Microsoft Office или книге Microsoft Excel, сначала создайте пользовательский элемент управления Windows Forms.  Затем добавьте пользовательский элемент управления со свойством <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> поля `ThisDocument.ActionsPane` \(слов\) или поля `ThisWorkbook.ActionsPane` \(Excel\) в проекте.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях.  Эти элементы определяются используемым выпуском Visual Studio и его параметрами.  Дополнительные сведения см. в разделе [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Создание пользовательского элемента управления  
 В следующей процедуре показано, как создать пользовательский элемент управления в проекте слова или Excel.  Она также добавить кнопку к пользовательскому элементу управления, который записывает текст в документ или книгу при ее нажата.  
  
#### Создание пользовательского элемента управления  
  
1.  Открытие проекта уровня документа на слова или Excel в Visual Studio.  
  
2.  В меню **Проект** выберите команду **Добавить новый элемент**.  
  
3.  В диалоговом окне **Добавление нового элемента** выберите **Элемент управления "Панель действий"**, дайте файлу имя **HelloControl** и нажмите кнопку **Добавить**.  
  
    > [!NOTE]  
    >  Можно также добавить в проект элемент **Пользовательский элемент управления**.  Классы, создаваемые элементами **Элемент управления панели действий** и **Пользовательский элемент управления**, функционально эквивалентны.  
  
4.  Со вкладки **Windows Forms** панели **Панель элементов** перетащите элемент управления **Кнопка** на элемент управления.  
  
    > [!NOTE]  
    >  Если элемент управления не виден в конструкторе, дважды щелкните **HelloControl** в **обозревателе решений**.  
  
5.  Добавьте код к обработчику событий <xref:System.Windows.Forms.Control.Click> кнопки.  Следующий код выставок примера документа слова Microsoft Office.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/HelloControl.vb#12)]  
  
6.  В C\# также необходимо добавить обработчик событий для события нажатия кнопки.  Этот код можно поместить в конструктор `HelloControl` после обращения к `IntializeComponent`.  
  
     Дополнительные сведения о создании обработчиков событий см. в разделе [Практическое руководство. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#13)]  
  
## Добавление пользовательского элемента управления в панель действий  
 Чтобы отобразить панель действий, добавьте пользовательский элемент управления со свойством <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> поля `ThisDocument.ActionsPane` \(слов\) или поля `ThisWorkbook.ActionsPane` \(Excel\).  
  
#### Добавление пользовательского элемента управления в панель действий  
  
1.  Добавьте следующий код в класс `ThisDocument` или `ThisWorkbook` в качестве объявления уровня класс\- \(не добавляйте этот код в метод\).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#14)]  
  
2.  Добавьте следующий код в обработчик событий `ThisDocument_Startup` класса `ThisDocument` или обработчик событий `ThisWorkbook_Startup` класса `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#15)]  
  
## См. также  
 [Общие сведения о панели действий](../vsto/actions-pane-overview.md)   
 [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Практическое руководство. Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  