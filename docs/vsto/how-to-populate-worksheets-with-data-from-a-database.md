---
title: Как выполнить Заполнение листов данными из базы данных
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 53267cdd429b9a4d8848026e460776359b55c023
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802878"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Как выполнить Заполнение листов данными из базы данных

Доступа к данным в проектах Office уровня документа можно таким же образом, что доступ к данным в проектах Windows Forms. Вы используете те же средства и код для получения данных в ваше решение и даже можете отображать данные с помощью элементов управления Windows Forms. Кроме того можно воспользоваться преимуществами элементов управления ведущего приложения, которые являются собственными объектами в Microsoft Office Excel, дополненные событиями и функциями привязки данных. Дополнительные сведения см. в разделе [ведущие элементы и размещать элементы управления](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

В следующем примере показано, как добавить элементы управления с привязкой к данным в проекты на уровне документа с помощью конструктора. Пример добавления элементов управления с привязкой к данным в проектах уровня приложения во время выполнения, см. в разделе [Пошаговое руководство: Сложная привязка данных в проекте надстройки VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

![ссылка на видео](../vsto/media/playvideo.gif "ссылка на видео") демонстрационные видеоматериалы см. в разделе [инструкции: Передавать данные на лист Excel? ](http://go.microsoft.com/fwlink/?LinkID=130277), и [инструкции: Использование данных базы данных в Excel? ](http://go.microsoft.com/fwlink/?LinkID=130287).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Добавление элемента управления с привязкой к данным на лист во время разработки

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Заполнение листов данными из базы данных

1.  Откройте проект уровня документа Excel в Visual Studio откройте лист в конструкторе.

2.  Откройте окно **Источники данных** и создайте источник данных для проекта. Дополнительные сведения см. в разделе [Добавление новых подключений](../data-tools/add-new-connections.md).

3.  Перетащите поле или таблицу, из **источников данных** окна на лист.

Один из следующих элементов управления создается на листе.

-   При перетаскивании поля, <xref:Microsoft.Office.Tools.Excel.NamedRange> создается элемент управления на листе. Дополнительные сведения см. в разделе [элемент управления NamedRange](../vsto/namedrange-control.md).

-   При перетаскивании таблицы, <xref:Microsoft.Office.Tools.Excel.ListObject> создается элемент управления на листе. Дополнительные сведения см. в разделе [элемент управления ListObject](../vsto/listobject-control.md).

Вы можете добавить другой элемент управления, выбрав таблицу или поле в **источников данных** окна и затем выбрав другой элемент управления из раскрывающегося списка.

## <a name="objects-in-the-project"></a>Объекты в проекте

Кроме элемента управления, в проект автоматически добавляются следующие объекты, связанные с данными.

-   Типизированный набор данных, который инкапсулирует таблицы данных, подключенные к базе данных. Дополнительные сведения см. в разделе [средства набора данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

-   Объект <xref:System.Windows.Forms.BindingSource>, который подключает элемент управления к типизированному набору данных. Дополнительные сведения см. в разделе [Общие сведения о компоненте BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

-   TableAdapter, который подключает типизированный набор данных в базу данных. Дополнительные сведения см. в разделе [TableAdapter overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

-   TableAdapterManager, который используется для координации адаптеров таблиц в наборе данных для реализации иерархических обновлений. Дополнительные сведения см. в разделе [иерархическое обновление](../data-tools/hierarchical-update.md) и [ссылку TableAdapterManager](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

При выполнении проекта элемент управления отображает первую запись в источнике данных. Вы можете использовать <xref:System.Windows.Forms.BindingSource>, чтобы позволить пользователям прокручивать записи.

### <a name="to-scroll-through-the-records"></a>Прокрутка записей

-   Используйте методы <xref:System.Windows.Forms.BindingSource>, такие как <xref:System.Windows.Forms.BindingSource.MoveNext%2A> и <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Сведения о том, как отправлять обновления типизированному набору данных и базе данных, см. в разделе [как: Обновить источник данных с данными из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>См. также

- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Добавление новых источников данных](../data-tools/add-new-data-sources.md)
- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Практическое руководство. Заполнение документов данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Практическое руководство. Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Практическое руководство. Заполнение документов данными из служб](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Практическое руководство. Обновить источник данных с данными из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Инструкции: Передавать данные на лист Excel](http://go.microsoft.com/fwlink/?LinkID=130277)
- [Инструкции: Использование данных базы данных в Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)