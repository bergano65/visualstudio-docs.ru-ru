---
title: "Элемент управления ListObject"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Toolbox.List"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "списки, события"
  - "ListObject - элемент управления"
  - "элемент управления ListObject, события"
  - "элемент управления ListObject, привязка данных"
  - "элемент управления ListObject, повышение производительности при выполнении привязки данных"
ms.assetid: 2bdecbf0-2a0f-48de-a544-dca12bb4a9a3
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Элемент управления ListObject
  Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> — это список с событиями, который может быть привязан к данным. При добавлении списка в лист Visual Studio создает элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject>, который можно запрограммировать напрямую, не обращаясь к объектной модели Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Создание элемента управления  
 В проектах уровня документа вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Excel.ListObject> в лист во время разработки или во время выполнения. В проектах надстроек VSTO вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Excel.ListObject> в листы только во время выполнения. Для получения дополнительной информации см. [Практическое руководство. Добавление элементов управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
> [!NOTE]  
>  По умолчанию при закрытии листа динамически созданные объекты списка не сохраняются в листе как элементы управления ведущего приложения. Для получения дополнительной информации см. [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## Привязка данных к элементу управления  
 Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> поддерживает как простую, так и сложную привязку данных. Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> можно привязать к источнику данных с помощью свойств <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> и <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> во время разработки или метода <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> во время выполнения.  
  
> [!NOTE]  
>  Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> обновляется автоматически, когда он привязан к источнику данных, например к объекту <xref:System.Data.DataTable>, который инициирует события при изменении данных. Если вы привязываете <xref:Microsoft.Office.Tools.Excel.ListObject> к источнику данных, который не инициирует события при изменении данных, необходимо вызывать метод <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> или <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> для обновления <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
 При добавлении <xref:Microsoft.Office.Tools.Excel.ListObject> в ячейку листа путем сопоставления повторяющегося элемента схемы с этой ячейкой Visual Studio автоматически сопоставляет <xref:Microsoft.Office.Tools.Excel.ListObject> с созданным набором данных. Однако автоматическая привязка <xref:Microsoft.Office.Tools.Excel.ListObject> к данным не выполняется. Вы можете выполнить ряд действий для привязки <xref:Microsoft.Office.Tools.Excel.ListObject> к набору данных во время разработки или во время выполнения в проекте уровня документа. Вы можете программными средствами привязать <xref:Microsoft.Office.Tools.Excel.ListObject> к набору данных во время выполнения в надстройке VSTO.  
  
 Поскольку данные существуют отдельно от <xref:Microsoft.Office.Tools.Excel.ListObject>, следует добавлять и удалять данные через привязанный набор данных, а не напрямую через <xref:Microsoft.Office.Tools.Excel.ListObject>. Если данные в привязанном наборе данных обновляются посредством какого\-либо механизма, элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> автоматически отражает изменения. Для получения дополнительной информации см. [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Можно быстро заполнить элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> путем привязки <xref:Microsoft.Office.Tools.Excel.ListObject> к источнику данных. При изменении данных в <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным эти изменения также автоматически вносятся в источник данных. Если вы хотите заполнить <xref:Microsoft.Office.Tools.Excel.ListObject>, а затем разрешить пользователю изменение данных в <xref:Microsoft.Office.Tools.Excel.ListObject> без изменения источника данных, можно использовать метод <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> для отключения <xref:Microsoft.Office.Tools.Excel.ListObject> от источника данных. Дополнительные сведения см. в разделе [Практическое руководство. Заполнение данными элементов управления ListObject](../vsto/how-to-fill-listobject-controls-with-data.md).  
  
> [!NOTE]  
>  Привязка данных в перекрывающихся элементах управления <xref:Microsoft.Office.Tools.Excel.ListObject> не поддерживается.  
  
### Повышение производительности в элементах управления ListObject  
 Считывание XML\-файла в элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным происходит довольно медленно, если сначала привязать элемент управления, а затем вызвать <xref:System.Data.DataSet.ReadXml%2A> для заполнения набора данных. Чтобы повысить производительность, вызывайте <xref:System.Data.DataSet.ReadXml%2A> перед привязкой элемента управления.  
  
### Отключение элементов управления ListObject от источника данных  
 После заполнения данными элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> путем его привязки к источнику данных вы можете отключить его, чтобы изменения, внесенные в данные в этом объекте\-списке, не влияли на источник данных. Дополнительные сведения см. в разделе [Практическое руководство. Заполнение данными элементов управления ListObject](../vsto/how-to-fill-listobject-controls-with-data.md).  
  
### Восстановление порядка строк и столбцов  
 При привязке данных к элементу управления <xref:Microsoft.Office.Tools.Excel.ListObject>, который был добавлен в документ во время разработки, Visual Studio отслеживает порядок столбцов и строк при каждом сохранении книги. Если пользователь перемещает столбцы или строки <xref:Microsoft.Office.Tools.Excel.ListObject> во время выполнения, новый порядок сохраняется при следующем открытии книги, и элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> снова привязывается к источнику данных.  
  
 Если вы хотите восстановить в <xref:Microsoft.Office.Tools.Excel.ListObject> исходный порядок строк и столбцов, можно вызвать метод <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A>. Этот метод удаляет свойства настраиваемого документа, относящиеся к порядку строк и столбцов указанного <xref:Microsoft.Office.Tools.Excel.ListObject>. Вызывайте этот метод из события <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> книги, если вы не хотите сохранять порядок строк и столбцов <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
## Форматирование  
 Любое форматирование, которое можно применить к <xref:Microsoft.Office.Interop.Excel.ListObject>, также можно применить и к элементу управления <xref:Microsoft.Office.Tools.Excel.ListObject>. Это включает границы, шрифты, формат чисел и стили. Конечные пользователи могут изменять порядок столбцов в <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным, и эти изменения будут сохранены в документе при условии, что <xref:Microsoft.Office.Tools.Excel.ListObject> был добавлен в документ во время разработки. При следующем открытии документа объект\-список будет привязан к тому же источнику данных, однако порядок столбцов будет отражать изменения пользователей.  
  
## Добавление и удаление столбцов во время выполнения  
 Вы не можете вручную добавлять или удалять столбцы в элементе управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным во время выполнения. Если конечный пользователь попытается удалить столбец, он будет сразу же восстановлен, а добавленные столбцы будут удалены. Таким образом, важно написать код, объясняющий пользователям, почему нельзя выполнять эти действия в элементе управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным. Visual Studio предоставляет в <xref:Microsoft.Office.Tools.Excel.ListObject> несколько событий, связанных с привязкой данных. Например, вы можете с помощью события <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> предупреждать пользователей, что данные, которые они пытались удалить, не подлежат удалению и были восстановлены.  
  
## Добавление и удаление строк во время выполнения  
 Вы можете вручную добавлять и удалять строки в элементе управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным, если источник данных позволяет добавлять новые строки и не предназначен только для чтения. Для проверки данных можно написать код для событий, таких как <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>. Для получения дополнительной информации см. [Практическое руководство. Обработка данных при добавлении новой строки в элемент управления ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md).  
  
 Иногда связь объекта списка с источником данных вызывает ошибки выполнения. Например, если указано, какие столбцы должны отображаться в <xref:Microsoft.Office.Tools.Excel.ListObject>, то при пропуске столбцов с ограничениями, такими как поле, не принимающее значения null, при каждом создании строки возникают ошибки. Вы можете написать код для добавления отсутствующих значений в обработчике событий для события <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>.  
  
## Переименование элементов управления ListObject в Excel  
 В Excel пользователи могут изменять имена таблиц Excel во время выполнения с помощью вкладки **Конструктор**. Однако элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> не поддерживает эту функцию. Если пользователь пытается переименовать таблицу Excel, которая соответствует <xref:Microsoft.Office.Tools.Excel.ListObject>, при сохранении книги будет автоматически восстановлено исходное имя таблицы Excel.  
  
## События  
 Для элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> доступны следующие события:  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>  
  
## См. также  
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Практическое руководство. Добавление элементов управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Практическое руководство. Изменение размера элементов управления ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Практическое руководство. Обработка данных при добавлении новой строки в элемент управления ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [Практическое руководство. Сопоставление столбцов элемента управления ListObject данным](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Практическое руководство. Заполнение данными элементов управления ListObject](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Практическое руководство. Заполнение листов данными из базы данных](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  