---
title: Добавление панели действий в документы Word или книги Excel
description: Сведения о том, как добавить панель действий в документ Word Microsoft Office или в книгу Microsoft Excel, необходимо сначала создать Windows Forms пользовательский элемент управления.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f9488a15f851446c5779bdb1a4572e69a1cf3053
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917519"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Практическое руководство. Добавление области действий в документы Word или книги Excel
  Чтобы добавить панель действий в Microsoft Office документ Word или книгу Microsoft Excel, сначала создайте пользовательский элемент управления Windows Forms. Затем добавьте пользовательский элемент управления в <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> свойство `ThisDocument.ActionsPane` поля (Word) или `ThisWorkbook.ActionsPane` FIELD (Excel) в проекте.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="creating-the-user-control"></a>Создание пользовательского элемента управления
 В следующей процедуре показано, как создать пользовательский элемент управления в проекте Word или Excel. Она также добавляет к пользовательскому элементу управления кнопку, которая записывает текст в документ или книгу при щелчке.

#### <a name="to-create-the-user-control"></a>Создание пользовательского элемента управления

1. Откройте проект уровня документа Word или Excel в Visual Studio.

2. В меню **Проект** выберите **Добавить новый элемент**.

3. В диалоговом окне **Добавление нового элемента** выберите **элемент Панель действий**, назовите его **хеллоконтрол** и нажмите кнопку **Добавить**.

    > [!NOTE]
    > Можно также добавить элемент **пользовательского элемента управления** в проект. Классы, созданные **элементом управления панели действий** и элементами **пользовательского элемента управления** , функционально эквивалентны.

4. На вкладке **Windows Forms** **панели элементов** перетащите элемент управления **Button** на элемент управления.

    > [!NOTE]
    > Если элемент управления не отображается в конструкторе, дважды щелкните **хеллоконтрол** в **Обозреватель решений**.

5. Добавьте код в <xref:System.Windows.Forms.Control.Click> обработчик событий кнопки. В следующем примере показан код для Microsoft Office документа Word.

     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]

6. В C# необходимо добавить обработчик событий для нажатия кнопки. Этот код можно поместить в `HelloControl` конструктор после вызова `InitializeComponent` .

     Дополнительные сведения о создании обработчиков событий см. в разделе [как создавать обработчики событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]

## <a name="add-the-user-control-to-the-actions-pane"></a>Добавление пользовательского элемента управления на панель действий
 Чтобы отобразить панель действий, добавьте пользовательский элемент управления в <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> свойство `ThisDocument.ActionsPane` поля (Word) или `ThisWorkbook.ActionsPane` FIELD (Excel).

### <a name="to-add-the-user-control-to-the-actions-pane"></a>Добавление пользовательского элемента управления на панель «действия»

1. Добавьте следующий код в `ThisDocument` класс или в `ThisWorkbook` качестве объявления уровня класса (не добавляйте этот код в метод).

     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]

2. Добавьте следующий код в `ThisDocument_Startup` обработчик событий `ThisDocument` класса или `ThisWorkbook_Startup` обработчика событий `ThisWorkbook` класса.

     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]

## <a name="see-also"></a>См. также раздел
- [Обзор панели действий](../vsto/actions-pane-overview.md)
- [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Руководство. Управление макетом элементов управления на панелях действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
