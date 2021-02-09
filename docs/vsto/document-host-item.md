---
title: Ведущий элемент документа
description: Сведения о том, что ведущий элемент документа — это тип, расширяющий тип документа из основной сборки взаимодействия для Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b7eb29a9cae9e43bd0372088298d2bd6b122c7a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910585"
---
# <a name="document-host-item"></a>Ведущий элемент документа
  Ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> является типом, который расширяет тип <xref:Microsoft.Office.Interop.Word.Document> из основной сборки взаимодействия для Word. Ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> предоставляет все свойства, методы и события объекта <xref:Microsoft.Office.Interop.Word.Document> , но также предоставляет дополнительные события и выступает в роли контейнера для элементов управления ведущего приложения и элементов управления Windows Forms.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 В проектах уровня документа имеется ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> по умолчанию, который представляет документ в проекте. В проектах надстройки VSTO во время выполнения можно создавать ведущие элементы <xref:Microsoft.Office.Tools.Word.Document> .

## <a name="understand-the-document-host-item-in-document-level-projects"></a>Знакомство с ведущим элементом документа в проектах уровня документа
 Для доступа к документу в проекте используйте класс `ThisDocument` . При создании проекта уровня документа Visual Studio создает класс `ThisDocument` в качестве связи между Word и кодом настройки. Класс `ThisDocument` обеспечивает доступ к членам ведущего элемента <xref:Microsoft.Office.Tools.Word.Document> для выполнения основных задач по настройке, например для запуска кода при открытии или закрытии документа. Вы также можете использовать эти классы для добавления элементов управления в документы. Используя различные сочетания элементов управления и создавая код, можно привязать элементы управления к данным, собирать сведения от пользователя и реагировать на действия пользователя. Дополнительные сведения см. в разделе [Program настройки на уровне документа](../vsto/programming-document-level-customizations.md).

 Класс `ThisDocument` предоставляет место, в котором можно начать создание кода в проекте. Поскольку этот класс предоставляет все свойства, методы и события, что и объект <xref:Microsoft.Office.Interop.Word.Document> в основной сборке взаимодействия для Word, вы также можете использовать `ThisDocument` для доступа к объектной модели Word. Дополнительные сведения см. в статье [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md).

### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Ограничения ведущего элемента документа в проектах уровня документа
 Проект уровня документа может содержать только один ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> (то есть класс `ThisDocument` ). Вы не можете добавлять новые ведущие элементы <xref:Microsoft.Office.Tools.Word.Document> в проект во время разработки и не можете создавать новые ведущие элементы <xref:Microsoft.Office.Tools.Word.Document> во время выполнения в настройке уровня документа.

 При создании нового документа Word во время выполнения он будет иметь тип <xref:Microsoft.Office.Interop.Word.Document>. Поскольку это не ведущий элемент, он не может содержать никаких элементов управления ведущего приложения или элементов управления Windows Forms. Дополнительные сведения о создании документов во время выполнения см. [в разделе инструкции. Программное создание новых документов](../vsto/how-to-programmatically-create-new-documents.md).

## <a name="understand-document-host-items-in-application-level-projects"></a>Общие сведения о ведущих элементах документов в проектах уровня приложения
 В проектах надстроек VSTO можно создавать ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> во время выполнения для любого документа, открытого в Word. Вы можете использовать ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> для добавления элементов управления в связанный документ или для обработки событий, которые недоступны в объектах <xref:Microsoft.Office.Interop.Word.Document> .

 Для создания ведущего элемента <xref:Microsoft.Office.Tools.Word.Document> используйте метод `GetVstoObject`. Дополнительные сведения см. [в разделе Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>См. также раздел
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
