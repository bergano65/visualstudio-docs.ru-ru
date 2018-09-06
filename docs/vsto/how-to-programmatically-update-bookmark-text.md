---
title: 'Практическое: программное обновление текста закладки'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aa4c2f37efe92bfbc3c06e0bc8f0657b1205652a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674001"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Практическое: программное обновление текста закладки
  Вы можете вставить текст в закладку-заполнитель в документе Microsoft Office Word, чтобы позднее извлечь или заменить текст закладки. При разработке настройки на уровне документа можно обновить текст в элементе управления <xref:Microsoft.Office.Tools.Word.Bookmark> с привязкой к данным. Дополнительные сведения см. в разделе [привязки данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Объект закладки может быть одного из двух типов.  
  
-   Элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> расширяют неуправляемые объекты <xref:Microsoft.Office.Interop.Word.Bookmark>, реализуя привязку к данным и предоставляя события. Дополнительные сведения об элементах управления ведущего приложения, см. в разделе [ведущие элементы и размещать элементы управления](../vsto/host-items-and-host-controls-overview.md).  
  
-   Собственный объект <xref:Microsoft.Office.Interop.Word.Bookmark>.  
  
     У объектов <xref:Microsoft.Office.Interop.Word.Bookmark> нет событий или возможностей для привязки данных.  
  
 Поведение <xref:Microsoft.Office.Interop.Word.Bookmark> и <xref:Microsoft.Office.Tools.Word.Bookmark> при назначении текста закладке отличается. Дополнительные сведения см. в разделе [элемент управления Bookmark](../vsto/bookmark-control.md).  
  
## <a name="use-host-controls"></a>Используйте элементы управления ведущего приложения  
  
### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Обновление содержимого закладки с помощью элемента управления Bookmark  
  
1.  Создайте процедуру, которая принимает аргумент `bookmark` в качестве имени закладки и аргумент `newText` в качестве строки, назначаемой свойству <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>.  
  
    > [!NOTE]  
    >  Назначение текста свойству <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> или <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> не приводит к удалению закладки.  
  
     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]  
  
2.  Назначить *newText* строка <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> свойство <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]  
  
## <a name="use-word-objects"></a>Использование объектов Word  
  
### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Обновление содержимого закладки с помощью объекта Bookmark приложения Word  
  
1.  Создайте процедуру, которая принимает аргумент `bookmark` в качестве имени <xref:Microsoft.Office.Interop.Word.Bookmark> и аргумент `newText` в качестве строки, назначаемой свойству <xref:Microsoft.Office.Interop.Word.Range.Text%2A> закладки.  
  
    > [!NOTE]  
    >  При присвоении текста собственному объекту <xref:Microsoft.Office.Interop.Word.Bookmark> Word закладка удаляется.  
  
     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]  
  
2.  Назначить *newText* строка <xref:Microsoft.Office.Interop.Word.Range.Text%2A> свойство закладки, что автоматически приведет к удалению закладки. Затем снова добавьте закладку в коллекцию <xref:Microsoft.Office.Interop.Word.Bookmarks>.  
  
     Следующий пример кода можно использовать в настройке на уровне документа.  
  
     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]  
  
     Следующий пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]  
  
## <a name="see-also"></a>См. также  
 [Практическое: программная Вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Обзор объектной модели Word](../vsto/word-object-model-overview.md)   
 [Элемент управления Bookmark](../vsto/bookmark-control.md)  
  
  