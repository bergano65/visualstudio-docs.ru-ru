---
title: "Ведущий элемент документа | Документы Microsoft"
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
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
ms.assetid: 4c1963f2-e88e-4c68-9f3d-13dedebddde4
caps.latest.revision: "47"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de243ee4b36d180b93e1b64f2a08c013a05d5360
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="document-host-item"></a>Ведущий элемент документа
  Ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> является типом, который расширяет тип <xref:Microsoft.Office.Interop.Word.Document> из основной сборки взаимодействия для Word. Ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> предоставляет все свойства, методы и события объекта <xref:Microsoft.Office.Interop.Word.Document> , но также предоставляет дополнительные события и выступает в роли контейнера для элементов управления ведущего приложения и элементов управления Windows Forms.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 В проектах уровня документа имеется ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> по умолчанию, который представляет документ в проекте. В проектах надстройки VSTO во время выполнения можно создавать ведущие элементы <xref:Microsoft.Office.Tools.Word.Document> .  
  
## <a name="understanding-the-document-host-item-in-document-level-projects"></a>Основные сведения о ведущих элементах документа в проектах уровня документа  
 Для доступа к документу в проекте используйте класс `ThisDocument` . При создании проекта уровня документа Visual Studio создает класс `ThisDocument` в качестве связи между Word и кодом настройки. Класс `ThisDocument` обеспечивает доступ к членам ведущего элемента <xref:Microsoft.Office.Tools.Word.Document> для выполнения основных задач по настройке, например для запуска кода при открытии или закрытии документа. Вы также можете использовать эти классы для добавления элементов управления в документы. Используя различные сочетания элементов управления и создавая код, можно привязать элементы управления к данным, собирать сведения от пользователя и реагировать на действия пользователя. Дополнительные сведения см. в разделе [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
 Класс `ThisDocument` предоставляет место, в котором можно начать создание кода в проекте. Поскольку этот класс предоставляет все свойства, методы и события, что и объект <xref:Microsoft.Office.Interop.Word.Document> в основной сборке взаимодействия для Word, вы также можете использовать `ThisDocument` для доступа к объектной модели Word. Дополнительные сведения см. в разделе [Word Object Model Overview](../vsto/word-object-model-overview.md).  
  
### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Ограничения ведущих элементов документа в проектах уровня документа  
 Проект уровня документа может содержать только один ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> (то есть класс `ThisDocument` ). Вы не можете добавлять новые ведущие элементы <xref:Microsoft.Office.Tools.Word.Document> в проект во время разработки и не можете создавать новые ведущие элементы <xref:Microsoft.Office.Tools.Word.Document> во время выполнения в настройке уровня документа.  
  
 При создании нового документа Word во время выполнения он будет иметь тип <xref:Microsoft.Office.Interop.Word.Document>. Поскольку это не ведущий элемент, он не может содержать никаких элементов управления ведущего приложения или элементов управления Windows Forms. Дополнительные сведения о создании документов во время выполнения см. в разделе [как: программным образом создавать новые документы](../vsto/how-to-programmatically-create-new-documents.md).  
  
## <a name="understanding-document-host-items-in-application-level-projects"></a>Основные сведения о ведущих элементах документов в проектах уровня приложения  
 В проектах надстроек VSTO можно создавать ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> во время выполнения для любого документа, открытого в Word. Вы можете использовать ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> для добавления элементов управления в связанный документ или для обработки событий, которые недоступны в объектах <xref:Microsoft.Office.Interop.Word.Document> .  
  
 Для создания <xref:Microsoft.Office.Tools.Word.Document> ведущий элемент, используйте метод GetVstoObject. Дополнительные сведения см. в разделе [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>См. также  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  