---
title: ListObject - элемент управления
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.List
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- lists, events
- ListObject control
- ListObject control, events
- ListObject control, data binding
- ListObject control, improving performance when bound to data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b5286a4bddff2b529abd0a565bb4dbeef7ffaf3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "71251868"
---
# <a name="listobject-control"></a>ListObject - элемент управления
  Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> — это список с событиями, который может быть привязан к данным. При добавлении списка в лист Visual Studio создает элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> , который можно запрограммировать напрямую, не обращаясь к объектной модели Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Создание элемента управления
 В проектах уровня документа вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Excel.ListObject> в лист во время разработки или во время выполнения. В проектах надстроек VSTO вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Excel.ListObject> в листы только во время выполнения. Дополнительные сведения см. [в разделе как добавить элементы управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md).

> [!NOTE]
> По умолчанию при закрытии листа динамически созданные объекты списка не сохраняются в листе как элементы управления ведущего приложения. Дополнительные сведения см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="bind-data-to-the-control"></a>Привязка данных к элементу управления
 Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> поддерживает как простую, так и сложную привязку данных. Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> можно привязать к источнику данных с помощью свойств <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> и <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> во время разработки или метода <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> во время выполнения.

> [!NOTE]
> Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> обновляется автоматически, когда он привязан к источнику данных, например к объекту <xref:System.Data.DataTable>, который инициирует события при изменении данных. Если вы привязываете <xref:Microsoft.Office.Tools.Excel.ListObject> к источнику данных, который не инициирует события при изменении данных, необходимо вызывать метод <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> или <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> для обновления <xref:Microsoft.Office.Tools.Excel.ListObject>.

 При добавлении <xref:Microsoft.Office.Tools.Excel.ListObject> в ячейку листа путем сопоставления повторяющегося элемента схемы с этой ячейкой Visual Studio автоматически сопоставляет <xref:Microsoft.Office.Tools.Excel.ListObject> с созданным набором данных. Однако автоматическая привязка <xref:Microsoft.Office.Tools.Excel.ListObject> к данным не выполняется. Вы можете выполнить ряд действий для привязки <xref:Microsoft.Office.Tools.Excel.ListObject> к набору данных во время разработки или во время выполнения в проекте уровня документа. Можно программно привязать <xref:Microsoft.Office.Tools.Excel.ListObject> к набору данных во время выполнения в надстройке VSTO.

 Поскольку данные существуют отдельно от <xref:Microsoft.Office.Tools.Excel.ListObject>, следует добавлять и удалять данные через привязанный набор данных, а не напрямую через <xref:Microsoft.Office.Tools.Excel.ListObject>. Если данные в привязанном наборе данных обновляются посредством какого-либо механизма, элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> автоматически отражает изменения. Дополнительные сведения см. [в разделе Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 Можно быстро заполнить элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> путем привязки <xref:Microsoft.Office.Tools.Excel.ListObject> к источнику данных. При изменении данных в <xref:Microsoft.Office.Tools.Excel.ListObject>с привязкой к данным эти изменения также автоматически вносятся в источник данных. Если вы хотите заполнить <xref:Microsoft.Office.Tools.Excel.ListObject> , а затем разрешить пользователю изменение данных в <xref:Microsoft.Office.Tools.Excel.ListObject> без изменения источника данных, можно использовать метод <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> для отключения <xref:Microsoft.Office.Tools.Excel.ListObject> от источника данных. Дополнительные сведения см. [в разделе инструкции. заполнение элементов управления ListObject данными](../vsto/how-to-fill-listobject-controls-with-data.md).

> [!NOTE]
> Привязка данных в перекрывающихся элементах управления <xref:Microsoft.Office.Tools.Excel.ListObject> не поддерживается.

### <a name="improve-performance-in-listobject-controls"></a>Повышение производительности в элементах управления ListObject
 Считывание XML-файла в элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным происходит довольно медленно, если сначала привязать элемент управления, а затем вызвать <xref:System.Data.DataSet.ReadXml%2A> для заполнения набора данных. Чтобы повысить производительность, вызывайте <xref:System.Data.DataSet.ReadXml%2A> перед привязкой элемента управления.

### <a name="disconnect-listobject-controls-from-the-data-source"></a>Отключение элементов управления ListObject от источника данных
 После заполнения данными элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> путем его привязки к источнику данных вы можете отключить его, чтобы изменения, внесенные в данные в этом объекте-списке, не влияли на источник данных. Дополнительные сведения см. [в разделе инструкции. заполнение элементов управления ListObject данными](../vsto/how-to-fill-listobject-controls-with-data.md).

### <a name="restore-column-and-row-order"></a>Восстановление порядка столбцов и строк
 При привязке данных к элементу управления <xref:Microsoft.Office.Tools.Excel.ListObject> , который был добавлен в документ во время разработки, Visual Studio отслеживает порядок столбцов и строк при каждом сохранении книги. Если пользователь перемещает столбцы или строки <xref:Microsoft.Office.Tools.Excel.ListObject> во время выполнения, новый порядок сохраняется при следующем открытии книги, и элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> снова привязывается к источнику данных.

 Если вы хотите восстановить в <xref:Microsoft.Office.Tools.Excel.ListObject> исходный порядок строк и столбцов, можно вызвать метод <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> . Этот метод удаляет свойства настраиваемого документа, относящиеся к порядку строк и столбцов указанного <xref:Microsoft.Office.Tools.Excel.ListObject>. Вызывайте этот метод из события <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> книги, если вы не хотите сохранять порядок строк и столбцов <xref:Microsoft.Office.Tools.Excel.ListObject>.

## <a name="format"></a>Формат
 Любое форматирование, которое можно применить к <xref:Microsoft.Office.Interop.Excel.ListObject> , также можно применить и к элементу управления <xref:Microsoft.Office.Tools.Excel.ListObject> . Это включает границы, шрифты, формат чисел и стили. Конечные пользователи могут изменять порядок столбцов в привязанных к данным данных <xref:Microsoft.Office.Tools.Excel.ListObject> , и эти изменения будут сохранены вместе с документом при условии, что элемент <xref:Microsoft.Office.Tools.Excel.ListObject> был добавлен в документ во время разработки. При следующем открытии документа объект-список будет привязан к тому же источнику данных, однако порядок столбцов будет отражать изменения пользователей.

## <a name="add-and-remove-columns-at-run-time"></a>Добавление и удаление столбцов во время выполнения
 Вы не можете вручную добавлять или удалять столбцы в элементе управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным во время выполнения. Если конечный пользователь пытается удалить столбец, он будет немедленно восстановлен, а все добавленные столбцы будут удалены. Таким образом, важно написать код, объясняющий пользователям, почему нельзя выполнять эти действия в элементе управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным. Visual Studio предоставляет в <xref:Microsoft.Office.Tools.Excel.ListObject> несколько событий, связанных с привязкой данных. Например, вы можете с помощью события <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> предупреждать пользователей, что данные, которые они пытались удалить, не подлежат удалению и были восстановлены.

## <a name="add-and-remove-rows-at-run-time"></a>Добавление и удаление строк во время выполнения
 Вы можете вручную добавлять и удалять строки в элементе управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным, если источник данных позволяет добавлять новые строки и не предназначен только для чтения. Для проверки данных можно написать код для событий, таких как <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> . Дополнительные сведения см. [в разделе инструкции. Проверка данных при добавлении новой строки в элемент управления ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md).

 Иногда связь объекта списка с источником данных вызывает ошибки выполнения. Например, если указано, какие столбцы должны отображаться в <xref:Microsoft.Office.Tools.Excel.ListObject>, то при пропуске столбцов с ограничениями, такими как поле, не принимающее значения null, при каждом создании строки возникают ошибки. Вы можете написать код для добавления отсутствующих значений в обработчике событий для события <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> .

## <a name="rename-listobject-controls-in-excel"></a>Переименование элементов управления ListObject в Excel
 Excel позволяет пользователям изменять имена таблиц Excel во время выполнения с помощью вкладки **конструктор** . Однако <xref:Microsoft.Office.Tools.Excel.ListObject> элемент управления не поддерживает эту функцию. Если пользователь пытается переименовать таблицу Excel, которая соответствует <xref:Microsoft.Office.Tools.Excel.ListObject>, при сохранении книги будет автоматически восстановлено исходное имя таблицы Excel.

## <a name="events"></a>События
 Для элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> доступны следующие события:

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Change>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>

## <a name="see-also"></a>См. также раздел
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Как добавить элементы управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Как изменить размер элементов управления ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Как проверить данные при добавлении новой строки в элемент управления ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Как сопоставлять столбцы ListObject с данными](../vsto/how-to-map-listobject-columns-to-data.md)
- [Как заполнить элементы управления ListObject данными](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Примеры и пошаговые руководства по разработке решений Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Как заполнить листы данными из базы данных](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
