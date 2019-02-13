---
title: Привязка элементов управления Windows Forms к данным
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6b961af0bf35bb4476f9f336fcf5298bb0bd3651
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951674"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Привязка элементов управления Windows Forms к данным в Visual Studio

Можно отобразить данные пользователям приложения путем привязки данных в формы Windows Forms. Чтобы создать эти элементы управления с привязкой к данным, перетащите элементы из **источников данных** на окно конструктора Windows Forms в Visual Studio.

![Операции перетаскивания источника данных](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Если **источников данных** окно не отображается, его можно открыть, выбрав **представление** > **Other Windows** > **источников данных** , или нажав **Shift**+**Alt**+**D**. Необходимо иметь открытый проект в Visual Studio для просмотра **источников данных** окна.

Прежде чем перетащить элементы, можно задать тип элемента управления, который вы хотите привязать к. В зависимости от того, самостоятельно, или отдельного столбца выбраны таблицы отображаются разные значения.  Можно также задать пользовательские значения. Для таблицы **сведения** означает, что каждый столбец привязан к отдельным элементом управления.

![Привязка источника данных к DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Элементы управления компонента BindingSource и BindingNavigator

Компонент <xref:System.Windows.Forms.BindingSource> служит двум целям. Во-первых он обеспечивает уровень абстракции, при привязке элементов управления к данным. Элементы управления в форме привязаны к <xref:System.Windows.Forms.BindingSource> компонента, а не непосредственно к источнику данных. Во-вторых он может управлять коллекцией объектов. Добавление типа для <xref:System.Windows.Forms.BindingSource> создает список этого типа.

Дополнительные сведения о <xref:System.Windows.Forms.BindingSource> компонента, см. в разделе:

- [Компонент BindingSource](/dotnet/framework/winforms/controls/bindingsource-component)

- [Общие сведения о компоненте BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [Архитектура компонента BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[Элемент управления BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) предоставляет пользовательский интерфейс для перехода по данным, отображаемым в приложении Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Привязка к данным в элементе управления DataGridView

Для [элемента управления DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), вся таблица привязана к этой одного элемента управления. При перетаскивании **DataGridView** в форму, средство удаления для перемещения по записям (<xref:System.Windows.Forms.BindingNavigator>) также отображается. Объект [набора данных](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов. На следующем рисунке [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) также добавляется, так как в таблице клиентов имеет отношение к таблице заказов. Эти переменные все объявляются в автоматически сформированном коде как закрытые члены в класс формы. Автоматически созданный код для заполнения **DataGridView** находится в `Form_Load` обработчик событий. Код для сохранения данных для обновления базы данных находится в `Save` обработчик событий для **BindingNavigator**. Можно переместить или изменить этот код как требуется.

![GridView с BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Можно настроить поведение **DataGridView** и **BindingNavigator** , щелкнув смарт-тега в правом верхнем углу каждого из них:

![DataGridView и привязка навигатор смарт-тегов](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Если элементы управления для приложения требуется не доступные в **источников данных** окно, вы можете добавить элементы управления. Дополнительные сведения см. в разделе [добавлять пользовательские элементы управления окна "Источники данных"](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Можно также перетаскивать элементы из **источников данных** окна на элементы управления на форму для привязки элемента управления к данным. Элемент управления, который уже привязан к данным содержит данные, восстанавливает привязку к элементу, наиболее недавно перетаскивания его. Допустимые конечные расположения сброса, элементы управления должны быть может отображать базовый тип данных элемента, перетаскиваемого в него из **источников данных** окна. Например, недопустимо перетащите элемент, имеющий тип данных <xref:System.DateTime> на <xref:System.Windows.Forms.CheckBox>, так как <xref:System.Windows.Forms.CheckBox> не способен отображать даты.

## <a name="bind-to-data-in-individual-controls"></a>Привязка к данным в отдельных элементах управления

При привязке источника данных для **сведения**, каждый столбец в наборе данных привязан к отдельным элементом управления.

![Привязка источника данных к сведения](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Обратите внимание, что на предыдущем рисунке, перетащите свойство Orders таблицы клиентов, а не из таблицы Orders. Путем привязки к `Customer.Orders` , команды навигации становятся **DataGridView** немедленно отражаются в элементы управления сведениями. Если перетащить из таблицы Orders, элементы управления будет по-прежнему связан с набором данных, но не они не будут синхронизированы с **DataGridView**.

На следующем рисунке показано значение по умолчанию элементы управления с привязкой к данным, которые добавляются в форму, после привязки к свойству Orders в таблице Customers **сведения** в **источников данных** окна.

![Таблица Orders, привязанного к сведения](../data-tools/media/raddata-orders-table-bound-to-details.png)

Обратите внимание, что каждый элемент управления имеет смарт-тег. Этот тег включает настройки, относящиеся к этому элементу управления только.

## <a name="see-also"></a>См. также

- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Привязка данных в Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)