---
title: Привязка элементов управления Windows Forms к данным в Visual Studio
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3d3226785724f6627a962c532cea29393eb5e46e
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747594"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Привязка элементов управления Windows Forms к данным в Visual Studio
Для пользователей приложения данные можно отображать путем привязки данных в Windows Forms. Чтобы создать эти элементы управления с привязкой к данным, можно перетаскивать элементы из **источники данных** окна в конструкторе Windows Forms в Visual Studio.

![Операции перетаскивания источника данных](../data-tools/media/raddata-data-source-drag-operation.png)

Прежде чем перетащить элементы, можно задать тип элемента управления, который вы хотите привязать к. В зависимости от того, выбрана ли таблица само себя или отдельного столбца отображаются различные значения.  Можно также задать значения по умолчанию. Для таблицы «Подробности» означает, что каждый столбец привязывается к отдельным элементом управления.

![Привязать источник данных к DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource и элементы управления BindingNavigator
Компонент <xref:System.Windows.Forms.BindingSource> служит двум целям. Во-первых он обеспечивает уровень абстракции, при выполнении привязки элементов управления к данным. Элементы управления в форме связаны с <xref:System.Windows.Forms.BindingSource> компонента, а не напрямую к источнику данных. Во-вторых он может управлять коллекцией объектов. Добавление типа в <xref:System.Windows.Forms.BindingSource> создает список этого типа.

Дополнительные сведения о <xref:System.Windows.Forms.BindingSource> компонента, см.:

-   [Компонент BindingSource](/dotnet/framework/winforms/controls/bindingsource-component)

-   [Общие сведения о компоненте BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)

-   [Архитектура компонента BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[Элемент управления BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) предоставляют пользовательский интерфейс для перемещения по данным, отображаемым в приложении Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Привязка к данным в элементе управления DataGridView
Для [элемента управления DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), вся таблица привязана к одного элемента управления. При перетаскивании элемента управления DataGridView в форму, средство удаления для перемещения по записям (<xref:System.Windows.Forms.BindingNavigator>) также отображается. Объект [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов. На следующем рисунке TableAdapterManager добавляется, так как в таблице Customers имеет отношение к таблице заказов. Эти переменные все объявляются в автоматически сформированном коде как закрытые члены в класс формы. Автоматически созданный код для заполнения DataGridView находится в обработчике событий form_load. Код для сохранения данных для обновления базы данных находится в обработчике событий Save для BindingNavigator. Можно переместить или изменить этот код как требуется.

![GridView с BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Можно настроить поведение DataGridView и BindingNavigator, щелкнув на смарт-тега в правом верхнем углу каждого:

![DataGridView и привязки навигатор смарт-теги](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Если элементы управления приложения требуется не доступен в **источники данных** окна, можно добавить элементы управления. Дополнительные сведения см. в разделе [добавить пользовательские элементы управления в окно источников данных](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Можно также перетаскивать элементы из **источники данных** окна на элементы управления на форму для привязки элемента управления к данным. Элемент управления, который уже привязан к данным содержит данные, восстанавливает привязку к элементу, недавно перетаскивания его. Допустимые целевые объекты перетаскивания, элементы управления должны быть рисунках базовый тип данных элемента, перетаскиваемые на него из **источники данных** окна. Например, не допускается перетащите элемент, имеющий тип данных <xref:System.DateTime> на <xref:System.Windows.Forms.CheckBox>, так как <xref:System.Windows.Forms.CheckBox> не может отображать даты.

## <a name="bind-to-data-in-individual-controls"></a>Привязка к данным в отдельных элементах управления
При привязке источника данных «Подробности», каждый столбец в наборе данных привязан к отдельным элементом управления.

![Привязать источник данных к подробные сведения](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Обратите внимание, что на предыдущем рисунке, перетащите из таблицы Customers, не из таблицы Orders свойства заказов. Путем привязки к свойству Customer.Orders команд перехода, внесенные в элемент управления DataGridView, немедленно отражаются в элементы управления сведениями. При перетаскивании таблицы Заказы, элементы управления по-прежнему будет привязываться к набору данных, но не они не будут синхронизированы с DataGridView.

На следующей иллюстрации по умолчанию элементы управления с привязкой к данным, которые добавляются в форму после свойство заказов в таблице Customers привязывается к «Подробности» в **источники данных** окна.

![Таблица Orders, привязанный к сведения](../data-tools/media/raddata-orders-table-bound-to-details.png)

Обратите внимание, что каждый элемент управления имеет смарт-тега. Этот тег включает настройки, относящиеся к этому элементу управления только.

## <a name="see-also"></a>См. также

- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Привязка данных в Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)