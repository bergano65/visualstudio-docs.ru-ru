---
title: Автоматизация Word с помощью расширенных объектов
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 85d3adc2ff156f6967d7590788c749d0343c7c0f
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248154"
---
# <a name="automate-word-by-using-extended-objects"></a>Автоматизация Word с помощью расширенных объектов
  При разработке решений Word в Visual Studio можно использовать *ведущие элементы* и *элементы управления ведущего приложения*в ваших решениях. Это объекты, которые расширяют некоторые часто используемые объекты в объектной модели Word (т. е. объектной модели, которая предоставляется основной сборкой взаимодействия для Word), такие как объекты <xref:Microsoft.Office.Interop.Word.Document> и <xref:Microsoft.Office.Interop.Word.ContentControl> . Расширенные объекты ведут себя как объекты Word, на которых они основаны, но добавляют объектам дополнительные события и возможности по привязке данных.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Ведущие элементы и элементы управления ведущего приложения доступны в надстройках VSTO и настройках на уровне документа, хотя контекст, в котором они используются, отличается для каждого типа решения. Дополнительные сведения см. в разделе [ведущие элементы и размещать элементы управления](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="document-host-item"></a>Ведущий элемент документа  
 Проекты Word предоставляют доступ к ведущим элементам <xref:Microsoft.Office.Tools.Word.Document> . Ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> служит контейнером для других элементов управления, в том числе элементов управления ведущего приложения и элементов управления Windows Forms, и хранит сведения об элементах управления на его поверхности. Ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> также предоставляет большинство тех же членов, что и класс <xref:Microsoft.Office.Interop.Word.Document> , который является классом-аналогом в объектной модели Word.  
  
 Дополнительные сведения см. в разделе [ведущий элемент документа](../vsto/document-host-item.md).  
  
## <a name="word-host-controls"></a>элементы управления ведущего приложения Word  
 Существует несколько элементов управления ведущего приложения для Word, которые помогают создавать, организовывать и автоматизировать документы. Основная их функциональность включает импорт, представление и защиту данных. Эти элементы управления ведущего приложения предоставляют события и возможности привязки к данным, не поддерживаемые их аналогами в управляемой объектной модели Word.  
  
 В проектах уровня документа можно добавить любой элемент управления ведущего приложения в документ во время разработки, или можно добавить элементы управления содержимым и элементы управления bookmark во время выполнения. В проектах надстройки VSTO можно добавить элементы управления содержимым и элементы управления bookmark в любой открытый документ во время выполнения.  
  
 Дополнительные сведения о ведущих элементах управления, которые можно использовать в проектах Word, см. в следующих разделах:  
  
-   [Элементы управления содержимым](../vsto/content-controls.md)  
  
-   [Элемент управления Bookmark](../vsto/bookmark-control.md)  
  
-   [Элемент управления XMLNode](../vsto/xmlnode-control.md)  
  
-   [Элемент управления XMLNodes](../vsto/xmlnodes-control.md)  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Практическое руководство. Добавление элементов управления Bookmark в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Практическое руководство. Добавление элементов управления XMLNode в документы Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Практическое руководство. Добавление элементов управления XMLNodes в документы Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Практическое руководство. Изменение размера элементов управления Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Пошаговое руководство. Создание шаблона с помощью элементов управления содержимым](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Пошаговое руководство. Привязка элементов управления содержимым к пользовательским XML-частям](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [Пошаговое руководство. Создать контекстное меню для закладок](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Решения Word](../vsto/word-solutions.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  