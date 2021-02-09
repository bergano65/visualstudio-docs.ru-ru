---
title: Как заполнить листы данными из базы данных
description: Узнайте, как можно использовать данные из объекта в решении и как использовать Windows Forms элементы управления для отображения данных на листе.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 66f37a1639cb6a86f107d9372704d5c8364c6a18
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918559"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Как заполнить листы данными из базы данных

Вы можете получить доступ к данным в проектах Office на уровне документа так же, как и к данным в Windows Forms проектах. Вы используете те же средства и код для получения данных в ваше решение и даже можете отображать данные с помощью элементов управления Windows Forms. Кроме того, можно воспользоваться элементами управления ведущего приложения, которые являются собственными объектами в Microsoft Office Excel, дополненными событиями и возможностями привязки данных. Дополнительные сведения см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

В следующем примере показано, как добавить элементы управления с привязкой к данным в проекты на уровне документа с помощью конструктора. Пример добавления элементов управления с привязкой к данным в проекты уровня приложения во время выполнения см. [в разделе Пошаговое руководство. сложная привязка данных в проекте надстройки VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Добавление привязанного к данным элемента управления на лист во время разработки

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Заполнение листа данными из базы данных

1. Откройте проект уровня документа Excel в Visual Studio и откройте лист в конструкторе.

2. Откройте окно **Источники данных** и создайте источник данных для проекта. Дополнительные сведения см. в разделе [Добавление новых соединений](../data-tools/add-new-connections.md).

3. Перетащите нужное поле или таблицу из окна **Источники данных** на лист.

На листе создается один из следующих элементов управления:

- При перетаскивании поля <xref:Microsoft.Office.Tools.Excel.NamedRange> на листе создается элемент управления. Дополнительные сведения см. в разделе [элемент управления NamedRange](../vsto/namedrange-control.md).

- При перетаскивании таблицы <xref:Microsoft.Office.Tools.Excel.ListObject> на листе создается элемент управления. Дополнительные сведения см. в разделе [элемент управления ListObject](../vsto/listobject-control.md).

Можно добавить другой элемент управления, выбрав таблицу или поле в окне **Источники данных** , а затем выбрав другой элемент управления из раскрывающегося списка.

## <a name="objects-in-the-project"></a>Объекты в проекте

Кроме элемента управления, в проект автоматически добавляются следующие объекты, связанные с данными.

- Типизированный набор данных, который инкапсулирует таблицы данных, подключенные к базе данных. Дополнительные сведения см. [в разделе Инструменты набора данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Объект <xref:System.Windows.Forms.BindingSource>, который подключает элемент управления к типизированному набору данных. Дополнительные сведения см. в разделе [Общие сведения о компоненте BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- Адаптер таблицы, который подключает типизированный набор данных к базе данных. Дополнительные сведения см. в разделе [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

- TableAdapterManager, который используется для координации адаптеров таблиц в наборе данных для включения иерархических обновлений. Дополнительные сведения см. в разделе [Иерархическое обновление](../data-tools/hierarchical-update.md) и [Справочник по TableAdapterManager](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

При выполнении проекта элемент управления отображает первую запись в источнике данных. Вы можете использовать <xref:System.Windows.Forms.BindingSource>, чтобы позволить пользователям прокручивать записи.

### <a name="to-scroll-through-the-records"></a>Прокрутка записей

- Используйте методы <xref:System.Windows.Forms.BindingSource>, такие как <xref:System.Windows.Forms.BindingSource.MoveNext%2A> и <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Сведения о том, как отправить обновления в типизированный набор данных и базу данных, см. в разделе [как обновить источник данных данными из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>См. также раздел

- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Добавление новых источников данных](../data-tools/add-new-data-sources.md)
- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Как заполнить документы данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Как заполнить документы данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Как заполнить документы данными из служб](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)