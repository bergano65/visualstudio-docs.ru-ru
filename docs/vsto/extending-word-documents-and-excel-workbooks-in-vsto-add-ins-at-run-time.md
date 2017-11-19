---
title: "Расширение документов Word и книг Excel в надстройках VSTO во время выполнения | Документы Microsoft"
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
- GetVstoObject method
- application-level add-ins [Office development in Visual Studio], adding controls to documents
- host items [Office development in Visual Studio], creating at run time in add-ins
- application-level add-ins [Office development in Visual Studio], extending Word documents
- application-level add-ins [Office development in Visual Studio], extending Excel workbooks
- controls [Office development in Visual Studio], adding at run time
- HasVstoObject method
ms.assetid: c1607314-4cf8-439c-b4c5-709db8b71cff
caps.latest.revision: "61"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93010f03384e3cb3930911115ee92b3bb9205b9e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time"></a>Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения
  Надстройку VSTO можно использовать для настройки документов Word и книг Excel одним из описанных ниже способов.  
  
-   Добавление управляемых элементов управления в любой открытый документ или лист.  
  
-   Преобразование существующего объекта списка на листе Excel в расширенный объект <xref:Microsoft.Office.Tools.Excel.ListObject> , который предоставляет события и позволяет выполнить привязку данных с помощью модели привязки данных Windows Forms.  
  
-   Получение доступа к событиям на уровне приложения, которые предоставляются Word и Excel для определенных документов, книг и листов.  
  
 Для использования данных функциональных возможностей необходимо в среде выполнения создать объект, расширяющий документ или книгу.  
  
 **Применимость.** Информация в этой статье относится к проектам надстроек VSTO для следующих приложений: Excel и Word. Для получения дополнительной информации см. [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
## <a name="generating-extended-objects-in-vsto-add-ins"></a>Создание расширенных объектов в надстройках VSTO  
 *Расширенные объекты* — это экземпляры типов, предоставляемых средой выполнения Visual Studio Tools для Office, и расширяющие функциональные возможности объектов, существующих в объектных моделях Word или Excel (так называемых *собственных объектов Office*). Чтобы создать расширенный объект для объекта Word или Excel, используйте метод GetVstoObject. При первом вызове метода GetVstoObject для указанного объекта Word или Excel он возвращает новый объект, расширяющий указанный объект. С каждым последующим вызовом этого метода для одного и того же объекта Word или Excel возвращается один и тот же расширенный объект.  
  
 Тип расширенного объекта имеет такое же имя, как тип собственного объекта Office, но этот тип определен в пространстве имен <xref:Microsoft.Office.Tools.Excel> или <xref:Microsoft.Office.Tools.Word> . Например, если вызвать метод GetVstoObject расширить <xref:Microsoft.Office.Interop.Word.Document> объекта, метод возвращает <xref:Microsoft.Office.Tools.Word.Document> объекта.  
  
 Методы GetVstoObject предназначены для использования преимущественно в проектах надстройки VSTO. Кроме того, их можно использовать в проектах уровня документа, но в этом случае они ведут себя иначе и имеют меньшее число применений.  
  
 Чтобы определить, создан ли уже расширенный объект для определенного собственного объекта Office, используйте HasVstoObject-метод. Дополнительные сведения см. в разделе [Определение факта расширения объекта Office](#HasVstoObject).  
  
### <a name="generating-host-items"></a>Создание ведущих элементов  
 При использовании GetVstoObject для расширения объекта уровня документа (то есть <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, или <xref:Microsoft.Office.Interop.Word.Document>), возвращаемый объект называется *ведущий элемент*. Ведущий элемент — это тип, который может содержать другие объекты, включая другие расширенные объекты и элементы управления. Ведущий элемент похож на соответствующий тип в основной сборке взаимодействия Word или Excel, но обладает дополнительными функциональными возможностями. Дополнительные сведения о ведущих элементах см. в разделе [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 Созданный ведущий документ можно использовать для добавления управляемых элементов управления в документ, книгу или лист. Дополнительные сведения см. в разделе [Добавление управляемых элементов управления в документы и листы](#AddControls).  
  
##### <a name="to-generate-a-host-item-for-a-word-document"></a>Создание ведущего элемента для документа Word  
  
-   В следующем примере кода показано, как создать ведущий элемент для активного документа.  
  
     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]  
  
##### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Создание ведущего элемента для книги Excel  
  
-   В следующем примере кода показано, как создать ведущий элемент для активной книги.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]  
  
##### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Создание ведущего элемента для листа Excel  
  
-   В следующем примере кода показано, как создать ведущий элемент для активного листа проекта.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]  
  
### <a name="generating-listobject-host-controls"></a>Создание элементов управления ведущего приложения ListObject  
 При использовании метода GetVstoObject расширить <xref:Microsoft.Office.Interop.Excel.ListObject>, метод возвращает <xref:Microsoft.Office.Tools.Excel.ListObject>. Объект <xref:Microsoft.Office.Tools.Excel.ListObject> обладает всеми функциональными возможностями исходного объекта <xref:Microsoft.Office.Interop.Excel.ListObject>, но также имеет дополнительные функциональные возможности, например возможность связывания с данными с использованием модели привязки данных Windows Forms. Для получения дополнительной информации см. [ListObject Control](../vsto/listobject-control.md).  
  
##### <a name="to-generate-a-host-control-for-a-listobject"></a>Создание элемента управления ведущего приложения для ListObject  
  
-   В следующем примере кода показано, как создать объект <xref:Microsoft.Office.Tools.Excel.ListObject> для первого объекта <xref:Microsoft.Office.Interop.Excel.ListObject> в активном листе проекта.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]  
  
##  <a name="AddControls"></a> Добавление управляемых элементов управления в документы и листы  
 После создания объекта <xref:Microsoft.Office.Tools.Word.Document> или <xref:Microsoft.Office.Tools.Excel.Worksheet>в документ или на лист можно добавить элементы управления, которым соответствуют эти расширенные объекты. Чтобы сделать это, используйте свойство элементов управления <xref:Microsoft.Office.Tools.Word.Document> или <xref:Microsoft.Office.Tools.Excel.Worksheet>. Дополнительные сведения см. в разделе [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Добавлять можно элементы управления Windows Forms или *элементы управления ведущего приложения*. Элемент управления ведущего приложения — это элемент управления, предоставляемый средой выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , которая упаковывает соответствующий элемент управления в основную сборку взаимодействия Word или Excel. Элемент управления ведущего приложения предоставляет все возможности, лежащие в основе собственного объекта Office, но, кроме того, вызывает события и может быть связан с данными с помощью модели привязки данных Windows Forms. Для получения дополнительной информации см. [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
> [!NOTE]  
>  Надстройка VSTO не позволяет добавить элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> на лист либо элемент управления <xref:Microsoft.Office.Tools.Word.XMLNode> или <xref:Microsoft.Office.Tools.Word.XMLNodes> в документ. Эти элементы управления ведущего приложения невозможно добавить программными средствами. Для получения дополнительной информации см. [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="persisting-and-removing-controls"></a>Сохранение и удаление элементов управления  
 Управляемые элементы управления, добавленные в документ или на лист, не сохраняются при сохранении и последующем закрытии документа. Все элементы управления удаляются; остаются только собственные объекты Office. Например, объект <xref:Microsoft.Office.Tools.Excel.ListObject> становится объектом <xref:Microsoft.Office.Interop.Excel.ListObject>. Все элементы управления Windows Forms также удаляются, но оболочки ActiveX для элементов управления в документе остаются. Для очистки элементов управления или повторного создания элементов управления при последующем открытии документа необходимо включить в надстройку соответствующий код. Дополнительные сведения см. в разделе [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
## <a name="accessing-application-level-events-on-documents-and-workbooks"></a>Получение доступа к событиям уровня приложения в документах и книгах  
 Некоторые события документа, книги и листа в собственных объектных моделях Word и Excel вызываются только на уровне приложения. Например, событие <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> вызывается при открытии документа в Word, но определяется в классе <xref:Microsoft.Office.Interop.Word.Application> , а не в классе <xref:Microsoft.Office.Interop.Word.Document> .  
  
 Если в надстройке VSTO используются только собственные объекты Office, необходимо обработать эти события уровня приложения, а затем написать дополнительный код, определяющий, является ли документ, который вызвал событие, одним из настроенных. Ведущие элементы предоставляют такие события на уровне документа; это упрощает обработку событий для конкретного документа. Также можно создать ведущий элемент, а затем обработать для него событие.  
  
### <a name="example-that-uses-native-word-objects"></a>Пример, в котором используются собственные объекты Word  
 В следующем примере кода показано, как обрабатывать событие уровня приложения для документов Word. Метод `CreateDocument` создает новый документ, а затем определяет обработчик событий <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> , который предотвращает сохранение этого документа. Поскольку это событие уровня приложения вызывается для объекта <xref:Microsoft.Office.Interop.Word.Application> , обработчик событий должен сравнить параметр `Doc` с объектом `document1` и определить, представляет ли `document1` сохраненный документ.  
  
 [!code-vb[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]  
  
### <a name="examples-that-use-a-host-item"></a>Примеры, в которых используется ведущий элемент  
 В следующем примере кода данная процедура упрощена за счет обработки события <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> ведущего документа <xref:Microsoft.Office.Tools.Word.Document> . В этих примерах метод `CreateDocument2` создает объект <xref:Microsoft.Office.Tools.Word.Document> , расширяющий объект `document2` , и затем определяет обработчик событий <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> , который предотвращает сохранение документа. Поскольку обработчик событий вызывается только при сохранении объекта `document2` , он может отменить действие сохранения, не выполняя дополнительные действия для верификации сохраняемого документа.  
  
 Следующий пример кода демонстрирует эту задачу.  
  
 [!code-vb[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]  
  
##  <a name="HasVstoObject"></a> Определение факта расширения объекта Office  
 Чтобы определить, создан ли уже расширенный объект для определенного собственного объекта Office, используйте HasVstoObject-метод. Этот метод возвращает значение **true** , если расширенный объект уже создан; в противном случае возвращается значение **false**.  
  
 Используйте метод Globals.Factory.HasVstoMethod. Передайте собственный объект Word или Excel (например, <xref:Microsoft.Office.Interop.Word.Document> или <xref:Microsoft.Office.Interop.Excel.Worksheet>), который необходимо протестировать для расширенного объекта.  
  
 Метод HasVstoObject полезен в тех случаях, когда требуется выполнить код только в том случае, если заданный объект Office имеет расширенный объект. Например, если у вас есть надстройки VSTO для Word, который обрабатывает <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> событий для удаления управляемых элементов управления из документа до сохранения, HasVstoObject-метод можно использовать, чтобы определить, расширялся ли документ. Если документ не расширялся, он не может содержать управляемые элементы управления, а следовательно, обработчик событий может не удалять элементы управления из документа.  
  
## <a name="see-also"></a>См. также  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md)  
  
  