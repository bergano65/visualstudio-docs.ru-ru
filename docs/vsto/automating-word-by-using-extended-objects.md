---
title: "Автоматизация Word с помощью расширенных объектов | Документы Microsoft"
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
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
ms.assetid: 3911c7cd-7092-468d-bd82-2fdec53a2d9b
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 89dde8238cd2badb4ea9841263d822b5729d00cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="automating-word-by-using-extended-objects"></a>Автоматизация Word с помощью расширенных объектов
  При разработке решений Word в Visual Studio можно использовать *ведущие элементы* и *элементы управления ведущего приложения*в ваших решениях. Это объекты, которые расширяют некоторые часто используемые объекты в объектной модели Word (т. е. объектной модели, которая предоставляется основной сборкой взаимодействия для Word), такие как объекты <xref:Microsoft.Office.Interop.Word.Document> и <xref:Microsoft.Office.Interop.Word.ContentControl> . Расширенные объекты ведут себя как объекты Word, на которых они основаны, но добавляют объектам дополнительные события и возможности по привязке данных.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Ведущие элементы и элементы управления ведущего приложения доступны в надстройках VSTO и настройках на уровне документа, хотя контекст, в котором они используются, отличается для каждого типа решения. Для получения дополнительной информации см. [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="document-host-item"></a>Ведущий элемент документа  
 Проекты Word предоставляют доступ к ведущим элементам <xref:Microsoft.Office.Tools.Word.Document> . Ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> служит контейнером для других элементов управления, в том числе элементов управления ведущего приложения и элементов управления Windows Forms, и хранит сведения об элементах управления на его поверхности. Ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> также предоставляет большинство тех же членов, что и класс <xref:Microsoft.Office.Interop.Word.Document> , который является классом-аналогом в объектной модели Word.  
  
 Дополнительные сведения см. в разделе [Document Host Item](../vsto/document-host-item.md).  
  
## <a name="word-host-controls"></a>Элементы управления ведущего приложения Word  
 Существует несколько элементов управления ведущего приложения для Word, которые помогают создавать, организовывать и автоматизировать документы. Основная их функциональность включает импорт, представление и защиту данных. Эти элементы управления ведущего приложения предоставляют события и возможности привязки к данным, не поддерживаемые их аналогами в управляемой объектной модели Word.  
  
 В проектах на уровне документа вы можете добавлять в документ любые элементы управления ведущего приложения во время разработки или добавлять элементы управления содержимым и элементы управления "закладка" во время выполнения. В проектах надстроек VSTO элементы управления содержимым и элементы управления "закладка" можно добавлять в любой открытый документ во время выполнения.  
  
 Дополнительные сведения о ведущих элементах управления, которые можно использовать в проектах Word, см. в следующих разделах:  
  
-   [Элементы управления содержимым](../vsto/content-controls.md)  
  
-   [Элемент управления Bookmark](../vsto/bookmark-control.md)  
  
-   [Элемент управления XMLNode](../vsto/xmlnode-control.md)  
  
-   [Элемент управления XMLNodes](../vsto/xmlnodes-control.md)  
  
## <a name="see-also"></a>См. также  
 [Как: Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Как: Добавление элементов управления XMLNode в документы Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Как: Добавление элементов управления XMLNodes в документы Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Как: изменение размеров элементов управления Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Пошаговое руководство: Создание шаблона с помощью элементов управления содержимым](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Пошаговое руководство: Привязка элементов управления содержимым к пользовательским XML-частям](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [Пошаговое руководство: Создание контекстного меню для закладок](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Решения Word](../vsto/word-solutions.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  