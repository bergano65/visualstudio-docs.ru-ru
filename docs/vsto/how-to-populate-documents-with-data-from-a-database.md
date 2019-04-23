---
title: Практическое руководство. Заполнение документов данными из базы данных
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4ec56ae4345405cfc704a97ec624f9c2e4d96a5b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061217"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Практическое руководство. Заполнение документов данными из базы данных

Доступ к данным в проектах уровня документа для Microsoft Office можно получить таким же образом, как при доступе к данным в проектах Windows Forms. Используйте те же средства и код для получения данных из базы данных в ваше решение. Также можно использовать элементы управления Windows Forms для отображения данных.

Кроме того, данные можно показать с помощью элементов управления ведущего приложения. Элементы управления ведущего приложения представляют собой управляемые объекты Microsoft Office Word, дополненные событиями и функциями привязки данных. Дополнительные сведения см. в разделе [ведущие элементы и размещать элементы управления](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

В следующем примере показано, как добавить элементы управления с привязкой к данным в проекты на уровне документа с помощью конструктора. Пример добавления элементов управления с привязкой к данным в проектах надстройки VSTO во время выполнения, см. в разделе [Пошаговое руководство: Простая привязка данных в проекте надстройки VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

![ссылка на видео](../vsto/media/playvideo.gif "ссылка на видео") демонстрационные видеоматериалы см. в разделе [привязка данных к содержимому Word 2007 элементы управления с помощью Visual Studio Tools для системы Office (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).

## <a name="add-a-control-to-a-document-at-design-time"></a>Добавление элемента управления в документ во время разработки

### <a name="to-populate-a-document-with-data-from-a-database"></a>Заполнение документа данными из базы данных

1. Откройте проект уровня документа Word в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и откройте документ в конструкторе.

2. Откройте **источников данных** окно и создать источник данных из базы данных. Дополнительные сведения см. в разделе [Добавление новых подключений](../data-tools/add-new-connections.md).

3. Перетащите поле из **источников данных** окно в документ.

В документ добавляется элемент управления содержимым. Тип элемента управления содержимым зависит от типа данных выбранного поля. Дополнительные сведения см. в разделе [элементы управления содержимым](../vsto/content-controls.md).

Можно добавить другой элемент управления, выбрав поле данных в **источников данных** окна и затем выбрав другой элемент управления из раскрывающегося списка.

## <a name="objects-in-the-project"></a>Объекты в проекте

Кроме элемента управления, в проект автоматически добавляются следующие объекты, связанные с данными.

- Типизированный набор данных, который инкапсулирует таблицы данных, подключенные к базе данных. Дополнительные сведения см. в разделе [средства набора данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Объект <xref:System.Windows.Forms.BindingSource>, который подключает элемент управления к типизированному набору данных. Дополнительные сведения см. в разделе [Общие сведения о компоненте BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- TableAdapter, который подключает типизированный набор данных в базу данных. Дополнительные сведения см. в разделе [Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md).

- TableAdapterManager, который используется для координации адаптеров таблиц в наборе данных для реализации иерархических обновлений. Дополнительные сведения см. в разделе [иерархическое обновление](../data-tools/hierarchical-update.md) и [ссылку TableAdapterManager](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

При выполнении проекта элемент управления отображает первую запись в источнике данных. Вы можете использовать <xref:System.Windows.Forms.BindingSource>, чтобы позволить пользователям прокручивать записи.

### <a name="to-scroll-through-the-records"></a>Прокрутка записей

- Используйте методы <xref:System.Windows.Forms.BindingSource>, такие как <xref:System.Windows.Forms.BindingSource.MoveNext%2A> и <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Сведения о том, как отправлять обновления типизированному набору данных и базе данных, см. в разделе [как: Обновить источник данных с данными из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>См. также

- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Добавление новых источников данных](../data-tools/add-new-data-sources.md)
- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Практическое руководство. Заполнение документов данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Практическое руководство. Обновить источник данных с данными из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Использовать файлы локальной базы данных в общие сведения о решений Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Общие сведения о компоненте BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)