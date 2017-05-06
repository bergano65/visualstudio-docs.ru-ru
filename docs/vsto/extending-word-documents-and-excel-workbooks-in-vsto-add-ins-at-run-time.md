---
title: "Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения"
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
  - "GetVstoObject - метод"
  - "надстройки уровня приложения [разработка решений Office в Visual Studio], добавление элементов управления в документы"
  - "ведущие элементы [разработка решений Office в Visual Studio], создание в надстройках во время выполнения"
  - "надстройки уровня приложения [разработка решений Office в Visual Studio], расширение документов Word"
  - "надстройки уровня приложения [разработка решений Office в Visual Studio], расширение книг Excel"
  - "элементы управления [разработка решений Office в Visual Studio], добавление во время выполнения"
  - "HasVstoObject - метод"
ms.assetid: c1607314-4cf8-439c-b4c5-709db8b71cff
caps.latest.revision: 61
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 60
---
# Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения
  Надстройку VSTO можно использовать для настройки документов Word и книг Excel одним из описанных ниже способов.  
  
-   Добавление управляемых элементов управления в любой открытый документ или лист.  
  
-   Преобразование существующего объекта списка на листе Excel в расширенный объект <xref:Microsoft.Office.Tools.Excel.ListObject>, который предоставляет события и позволяет выполнить привязку данных с помощью модели привязки данных Windows Forms.  
  
-   Получение доступа к событиям на уровне приложения, которые предоставляются Word и Excel для определенных документов, книг и листов.  
  
 Для использования данных функциональных возможностей необходимо в среде выполнения создать объект, расширяющий документ или книгу.  
  
 **Применимость.** Информация в этой статье относится к проектам надстроек VSTO для следующих приложений: Excel и Word. Для получения дополнительной информации см. [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).  
  
## Создание расширенных объектов в надстройках VSTO  
 *Расширенные объекты* — это экземпляры типов, предоставляемых средой выполнения Visual Studio Tools для Office, и расширяющие функциональные возможности объектов, существующих в объектных моделях Word или Excel \(так называемых *собственных объектов Office*\). Чтобы создать расширенный объект для объекта Word или Excel, используйте метод GetVstoObject. При первом вызове метода GetVstoObject для указанного объекта Word или Excel он возвращает новый объект, расширяющий указанный объект. С каждым последующим вызовом этого метода для одного и того же объекта Word или Excel возвращается один и тот же расширенный объект.  
  
 Тип расширенного объекта имеет такое же имя, как тип собственного объекта Office, но этот тип определен в пространстве имен <xref:Microsoft.Office.Tools.Excel> или <xref:Microsoft.Office.Tools.Word>. Например, если метод GetVstoObject вызывается для расширения объекта <xref:Microsoft.Office.Interop.Word.Document>, он возвращает объект <xref:Microsoft.Office.Tools.Word.Document>.  
  
 Методы GetVstoObject предназначены для использования преимущественно в проектах надстроек VSTO. Кроме того, их можно использовать в проектах уровня документа, но в этом случае они ведут себя иначе и имеют меньшее число применений.  
  
 Чтобы определить, создан ли уже расширенный объект для определенного собственного объекта Office, воспользуйтесь методом HasVstoObject. Дополнительные сведения см. в разделе [Определение факта расширения объекта Office](#HasVstoObject).  
  
### Создание ведущих элементов  
 Если метод GetVstoObject используется для расширения объекта уровня документа \(т. е. <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet> или <xref:Microsoft.Office.Interop.Word.Document>\), возвращаемый объект называется *ведущим элементом*. Ведущий элемент — это тип, который может содержать другие объекты, включая другие расширенные объекты и элементы управления. Ведущий элемент похож на соответствующий тип в основной сборке взаимодействия Word или Excel, но обладает дополнительными функциональными возможностями. Дополнительные сведения о ведущих элементах см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).  
  
 Созданный ведущий документ можно использовать для добавления управляемых элементов управления в документ, книгу или лист. Дополнительные сведения см. в разделе [Добавление управляемых элементов управления в документы и листы](#AddControls).  
  
##### Создание ведущего элемента для документа Word  
  
-   В следующем примере кода показано, как создать ведущий элемент для активного документа.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_WordAddInDynamicControls#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#8)]  
  
##### Создание ведущего элемента для книги Excel  
  
-   В следующем примере кода показано, как создать ведущий элемент для активной книги.  
  
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/VB/ThisAddIn.vb#2)]  
  
##### Создание ведущего элемента для листа Excel  
  
-   В следующем примере кода показано, как создать ведущий элемент для активного листа проекта.  
  
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/VB/ThisAddIn.vb#1)]  
  
### Создание элементов управления ведущего приложения ListObject  
 Если метод GetVstoObject используется для расширения объекта <xref:Microsoft.Office.Interop.Excel.ListObject>, возвращается объект <xref:Microsoft.Office.Tools.Excel.ListObject>. Объект <xref:Microsoft.Office.Tools.Excel.ListObject> обладает всеми функциональными возможностями исходного объекта <xref:Microsoft.Office.Interop.Excel.ListObject>, но также имеет дополнительные функциональные возможности, например возможность связывания с данными с использованием модели привязки данных Windows Forms. Для получения дополнительной информации см. [Элемент управления ListObject](../vsto/listobject-control.md).  
  
##### Создание элемента управления ведущего приложения для ListObject  
  
-   В следующем примере кода показано, как создать объект <xref:Microsoft.Office.Tools.Excel.ListObject> для первого объекта <xref:Microsoft.Office.Interop.Excel.ListObject> в активном листе проекта.  
  
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/VB/ThisAddIn.vb#3)]  
  
##  <a name="AddControls"></a> Добавление управляемых элементов управления в документы и листы  
 После создания объекта <xref:Microsoft.Office.Tools.Word.Document> или <xref:Microsoft.Office.Tools.Excel.Worksheet> в документ или на лист можно добавить элементы управления, которым соответствуют эти расширенные объекты. Для этого воспользуйтесь свойством Controls объекта <xref:Microsoft.Office.Tools.Word.Document> или <xref:Microsoft.Office.Tools.Excel.Worksheet>. Дополнительные сведения см. в разделе [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Добавлять можно элементы управления Windows Forms или *элементы управления ведущего приложения*. Элемент управления ведущего приложения — это элемент управления, предоставляемый средой выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], которая упаковывает соответствующий элемент управления в основную сборку взаимодействия Word или Excel. Элемент управления ведущего приложения предоставляет все возможности, лежащие в основе собственного объекта Office, но, кроме того, вызывает события и может быть связан с данными с помощью модели привязки данных Windows Forms. Для получения дополнительной информации см. [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).  
  
> [!NOTE]  
>  Надстройка VSTO не позволяет добавить элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> на лист либо элемент управления <xref:Microsoft.Office.Tools.Word.XMLNode> или <xref:Microsoft.Office.Tools.Word.XMLNodes> в документ. Эти элементы управления ведущего приложения невозможно добавить программными средствами. Для получения дополнительной информации см. [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### Сохранение и удаление элементов управления  
 Управляемые элементы управления, добавленные в документ или на лист, не сохраняются при сохранении и последующем закрытии документа. Все элементы управления удаляются; остаются только собственные объекты Office. Например, объект <xref:Microsoft.Office.Tools.Excel.ListObject> становится объектом <xref:Microsoft.Office.Interop.Excel.ListObject>. Все элементы управления Windows Forms также удаляются, но оболочки ActiveX для элементов управления в документе остаются. Для очистки элементов управления или повторного создания элементов управления при последующем открытии документа необходимо включить в надстройку соответствующий код. Дополнительные сведения см. в разделе [Сохранение динамических элементов управления в документах Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
## Получение доступа к событиям уровня приложения в документах и книгах  
 Некоторые события документа, книги и листа в собственных объектных моделях Word и Excel вызываются только на уровне приложения. Например, событие <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> вызывается при открытии документа в Word, но определяется в классе <xref:Microsoft.Office.Interop.Word.Application>, а не в классе <xref:Microsoft.Office.Interop.Word.Document>.  
  
 Если в надстройке VSTO используются только собственные объекты Office, необходимо обработать эти события уровня приложения, а затем написать дополнительный код, определяющий, является ли документ, который вызвал событие, одним из настроенных. Ведущие элементы предоставляют такие события на уровне документа; это упрощает обработку событий для конкретного документа. Также можно создать ведущий элемент, а затем обработать для него событие.  
  
### Пример, в котором используются собственные объекты Word  
 В следующем примере кода показано, как обрабатывать событие уровня приложения для документов Word. Метод `CreateDocument` создает новый документ, а затем определяет обработчик событий <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>, который предотвращает сохранение этого документа. Поскольку это событие уровня приложения вызывается для объекта <xref:Microsoft.Office.Interop.Word.Application>, обработчик событий должен сравнить параметр `Doc` с объектом `document1` и определить, представляет ли `document1` сохраненный документ.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#12)]
 [!code-vb[Trin_WordAddInDynamicControls#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#12)]  
  
### Примеры, в которых используется ведущий элемент  
 В следующем примере кода данная процедура упрощена за счет обработки события <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> ведущего документа <xref:Microsoft.Office.Tools.Word.Document>. В этих примерах метод `CreateDocument2` создает объект <xref:Microsoft.Office.Tools.Word.Document>, расширяющий объект `document2`, и затем определяет обработчик событий <xref:Microsoft.Office.Tools.Word.Document.BeforeSave>, который предотвращает сохранение документа. Поскольку обработчик событий вызывается только при сохранении объекта `document2`, он может отменить действие сохранения, не выполняя дополнительные действия для верификации сохраняемого документа.  
  
 Следующий пример кода демонстрирует эту задачу.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#13)]
 [!code-vb[Trin_WordAddInDynamicControls#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#13)]  
  
##  <a name="HasVstoObject"></a> Определение факта расширения объекта Office  
 Чтобы определить, создан ли уже расширенный объект для определенного собственного объекта Office, воспользуйтесь методом HasVstoObject. Этот метод возвращает значение **true**, если расширенный объект уже создан; в противном случае возвращается значение **false**.  
  
 Воспользуйтесь методом Globals.Factory.HasVstoMethod. Передайте собственный объект Word или Excel \(например, <xref:Microsoft.Office.Interop.Word.Document> или <xref:Microsoft.Office.Interop.Excel.Worksheet>\), который необходимо протестировать для расширенного объекта.  
  
 Метод HasVstoObject полезен в ситуации, когда код необходимо запускать только при условии, что заданный объект Office имеет расширенный объект. Например, если надстройка VSTO для Word обрабатывает событие <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> для удаления управляемых элементов управления из документа до сохранения, с помощью метода HasVstoObject можно определить, расширялся ли соответствующий документ. Если документ не расширялся, он не может содержать управляемые элементы управления, а следовательно, обработчик событий может не удалять элементы управления из документа.  
  
## См. также  
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md)  
  
  