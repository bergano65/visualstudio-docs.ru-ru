---
title: Расширение документов Word и книг Excel в надстройках VSTO во время выполнения
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- GetVstoObject method
- application-level add-ins [Office development in Visual Studio], adding controls to documents
- host items [Office development in Visual Studio], creating at run time in add-ins
- application-level add-ins [Office development in Visual Studio], extending Word documents
- application-level add-ins [Office development in Visual Studio], extending Excel workbooks
- controls [Office development in Visual Studio], adding at run time
- HasVstoObject method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2058029bfc188cd3284768e3d1782f7cda96c5c1
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402111"
---
# <a name="extend-word-documents-and-excel-workbooks-in-vsto-add-ins-at-runtime"></a>Расширение документов Word и книг Excel в надстройках VSTO во время выполнения
  Надстройку VSTO можно использовать для настройки документов Word и книг Excel одним из описанных ниже способов.

- Добавление управляемых элементов управления в любой открытый документ или лист.

- Преобразование существующего объекта списка на листе Excel в расширенный объект <xref:Microsoft.Office.Tools.Excel.ListObject> , который предоставляет события и позволяет выполнить привязку данных с помощью модели привязки данных Windows Forms.

- Получение доступа к событиям на уровне приложения, которые предоставляются Word и Excel для определенных документов, книг и листов.

  Чтобы использовать эту функцию, создается объект во время выполнения, расширяющий документ или книгу.

  **Область применения:** Сведения в этой статье, относятся к проектам надстроек VSTO для следующих приложений: Excel и Word. Дополнительные сведения см. в разделе [функций по типам приложений и проектов Office](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="generate-extended-objects-in-vsto-add-ins"></a>Создание расширенных объектов в надстройках VSTO
 *Расширенные объекты* — это экземпляры типов, предоставляемых средой выполнения Visual Studio Tools для Office, и расширяющие функциональные возможности объектов, существующих в объектных моделях Word или Excel (так называемых *собственных объектов Office*). Чтобы создать расширенный объект для объекта Word или Excel, используйте метод `GetVstoObject`. При первом вызове `GetVstoObject` объект метода для указанного Word или Excel, он возвращает новый объект, расширяющий указанный объект. С каждым последующим вызовом этого метода для одного и того же объекта Word или Excel возвращается один и тот же расширенный объект.

 Тип расширенного объекта имеет такое же имя, как тип собственного объекта Office, но этот тип определен в пространстве имен <xref:Microsoft.Office.Tools.Excel> или <xref:Microsoft.Office.Tools.Word> . Например, если метод `GetVstoObject` вызывается для расширения объекта <xref:Microsoft.Office.Interop.Word.Document>, он возвращает объект <xref:Microsoft.Office.Tools.Word.Document>.

 Методы `GetVstoObject` предназначены для использования преимущественно в проектах надстроек VSTO. Кроме того, их можно использовать в проектах уровня документа, но в этом случае они ведут себя иначе и имеют меньшее число применений.

 Чтобы определить, создан ли уже расширенный объект для определенного собственного объекта Office, воспользуйтесь методом `HasVstoObject`. Дополнительные сведения см. в разделе [определить, ли расширения объекта Office](#HasVstoObject).

### <a name="generate-host-items"></a>Создание ведущих элементов
 При использовании `GetVstoObject` для расширения объекта уровня документа (т. е <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, или <xref:Microsoft.Office.Interop.Word.Document>), возвращаемый объект называется *ведущий элемент*. Ведущий элемент — это тип, который может содержать другие объекты, включая другие расширенные объекты и элементы управления. Ведущий элемент похож на соответствующий тип в основной сборке взаимодействия Word или Excel, но обладает дополнительными функциональными возможностями. Дополнительные сведения о ведущих элементах см. в разделе [ведущие элементы и размещать элементы управления](../vsto/host-items-and-host-controls-overview.md).

 Созданный ведущий документ можно использовать для добавления управляемых элементов управления в документ, книгу или лист. Дополнительные сведения см. в разделе [Добавление управляемых элементов управления в документы и листы](#AddControls).

#### <a name="to-generate-a-host-item-for-a-word-document"></a>Создание ведущего элемента для документа Word

- В следующем примере кода показано, как создать ведущий элемент для активного документа.

     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]

#### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Создание ведущего элемента для книги Excel

- В следующем примере кода показано, как создать ведущий элемент для активной книги.

     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]

#### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Создание ведущего элемента для листа Excel

- В следующем примере кода показано, как создать ведущий элемент для активного листа проекта.

     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]

### <a name="generate-listobject-host-controls"></a>Создание элементов управления ведущего приложения ListObject
 Если метод `GetVstoObject` используется для расширения объекта <xref:Microsoft.Office.Interop.Excel.ListObject>, возвращается объект <xref:Microsoft.Office.Tools.Excel.ListObject>. <xref:Microsoft.Office.Tools.Excel.ListObject> Обладает всеми возможностями исходного <xref:Microsoft.Office.Interop.Excel.ListObject>. Он также имеет дополнительные функциональные возможности и может быть привязан к данным с помощью модели привязки данных Windows Forms. Дополнительные сведения см. в разделе [элемент управления ListObject](../vsto/listobject-control.md).

#### <a name="to-generate-a-host-control-for-a-listobject"></a>Создание элемента управления ведущего приложения для ListObject

- В следующем примере кода показано, как создать объект <xref:Microsoft.Office.Tools.Excel.ListObject> для первого объекта <xref:Microsoft.Office.Interop.Excel.ListObject> в активном листе проекта.

     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]

### <a name="AddControls"></a> Добавление управляемых элементов управления в документы и листы
 После создания объекта <xref:Microsoft.Office.Tools.Word.Document> или <xref:Microsoft.Office.Tools.Excel.Worksheet>в документ или на лист можно добавить элементы управления, которым соответствуют эти расширенные объекты. Чтобы добавить элементы управления, используйте `Controls` свойство <xref:Microsoft.Office.Tools.Word.Document> или <xref:Microsoft.Office.Tools.Excel.Worksheet>. Дополнительные сведения см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Добавлять можно элементы управления Windows Forms или *элементы управления ведущего приложения*. Элемент управления ведущего приложения — это элемент управления, предоставляемый средой выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , которая упаковывает соответствующий элемент управления в основную сборку взаимодействия Word или Excel. Элемент управления ведущего приложения предоставляет все поведение базовый собственный объект Office. Он также создает события и может быть привязан к данным с помощью модели привязки данных Windows Forms. Дополнительные сведения см. в разделе [ведущие элементы и размещать элементы управления](../vsto/host-items-and-host-controls-overview.md).

> [!NOTE]
> Надстройка VSTO не позволяет добавить элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> на лист либо элемент управления <xref:Microsoft.Office.Tools.Word.XMLNode> или <xref:Microsoft.Office.Tools.Word.XMLNodes> в документ. Эти элементы управления ведущего приложения невозможно добавить программными средствами. Дополнительные сведения см. в разделе [программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

### <a name="persist-and-remove-controls"></a>Сохранение и удаление элементов управления
 Управляемые элементы управления, добавленные в документ или на лист, не сохраняются при сохранении и последующем закрытии документа. Все элементы управления удаляются; остаются только собственные объекты Office. Например, объект <xref:Microsoft.Office.Tools.Excel.ListObject> становится объектом <xref:Microsoft.Office.Interop.Excel.ListObject>. Все элементы управления Windows Forms также удаляются, но оболочки ActiveX для элементов управления в документе остаются. Для очистки элементов управления или повторного создания элементов управления при последующем открытии документа необходимо включить в надстройку соответствующий код. Дополнительные сведения см. в разделе [сохранение динамических элементов управления в документы Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

## <a name="access-application-level-events-on-documents-and-workbooks"></a>События уровня приложения доступа в документах и книгах
 Некоторые события документа, книги и листа в собственных объектных моделях Word и Excel вызываются только на уровне приложения. Например, событие <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> вызывается при открытии документа в Word, но определяется в классе <xref:Microsoft.Office.Interop.Word.Application> , а не в классе <xref:Microsoft.Office.Interop.Word.Document> .

 Если в надстройке VSTO используются только собственные объекты Office, необходимо обработать эти события уровня приложения, а затем написать дополнительный код, определяющий, является ли документ, который вызвал событие, одним из настроенных. Ведущие элементы предоставляют такие события на уровне документа; это упрощает обработку событий для конкретного документа. Также можно создать ведущий элемент, а затем обработать для него событие.

### <a name="example-that-uses-native-word-objects"></a>Пример, использующий собственные объекты Word
 В следующем примере кода показано, как обрабатывать событие уровня приложения для документов Word. Метод `CreateDocument` создает новый документ, а затем определяет обработчик событий <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> , который предотвращает сохранение этого документа. Это событие уровня приложения вызывается для <xref:Microsoft.Office.Interop.Word.Application> объект и обработчик событий должен сравнить `Doc` параметр с `document1` объекта на предмет `document1` представляет сохраненный документ.

 [!code-vb[Trin_WordAddInDynamicControls #12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]

### <a name="examples-that-use-a-host-item"></a>Примеры, в которых используется ведущий элемент
 В следующем примере кода данная процедура упрощена за счет обработки события <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> ведущего документа <xref:Microsoft.Office.Tools.Word.Document> . `CreateDocument2` Создает метод в этих примерах <xref:Microsoft.Office.Tools.Word.Document> , расширяющий `document2` объекта, а затем определяет <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> обработчик событий, который предотвращает сохранение документа. Обработчик событий вызывается только тогда, когда `document2` сохраняется, а также может отменить сохранение действия без выполнения дополнительных действий для проверки документа, который был сохранен.

 Следующий пример кода демонстрирует эту задачу.

 [!code-vb[Trin_WordAddInDynamicControls #13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]

## <a name="HasVstoObject"></a> Определить, ли расширения объекта Office
 Чтобы определить, создан ли уже расширенный объект для определенного собственного объекта Office, воспользуйтесь методом `HasVstoObject`. Этот метод возвращает **true** Если расширенный объект уже создан.

 Воспользуйтесь методом `Globals.Factory.HasVstoMethod`. Передайте собственный объект Word или Excel (например, <xref:Microsoft.Office.Interop.Word.Document> или <xref:Microsoft.Office.Interop.Excel.Worksheet>), который необходимо протестировать для расширенного объекта.

 Метод `HasVstoObject` полезен в ситуации, когда код необходимо запускать только при условии, что заданный объект Office имеет расширенный объект. Например, если у вас есть надстройки VSTO для Word, который обрабатывает <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> событий для удаления управляемых элементов управления из документа до его сохранения, используйте `HasVstoObject` метод, чтобы определить, расширен ли документ. Если документ не была расширена, он не может иметь управляемых элементов управления, и обработчик событий может возвращать без попытки очистить элементы управления из документа.

## <a name="see-also"></a>См. также
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)
- [Примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md)
