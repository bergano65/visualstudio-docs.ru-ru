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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 244829edb30bbd43384ba445852f0a9ceafafb3f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587021"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Привязка элементов управления Windows Forms к данным в Visual Studio

Вы можете отображать данные для пользователей приложения, привязывая данные к Windows Forms. Чтобы создать эти элементы управления с привязкой к данным, перетащите элементы из окна **Источники данных** на конструктор Windows Forms в Visual Studio.

![Операция перетаскивания источника данных](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Если окно **Источники данных** не отображается, его можно открыть, выбрав **вид** > другие > **Источники данных** **Windows** или нажав клавиши **SHIFT**+**ALT**+**D**. Для просмотра окна **Источники данных** в Visual Studio должен быть открыт проект.

Перед перетаскиванием элементов можно задать тип элемента управления, к которому необходимо выполнить привязку. Различные значения отображаются в зависимости от выбора самой таблицы или отдельного столбца.  Можно также задать пользовательские значения. Для таблицы **сведения** означает, что каждый столбец привязан к отдельному элементу управления.

![Привязка источника данных к DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Элементы управления BindingSource и BindingNavigator

Компонент <xref:System.Windows.Forms.BindingSource> служит двум целям. Во-первых, он предоставляет уровень абстракции при привязке элементов управления к данным. Элементы управления формы привязаны к <xref:System.Windows.Forms.BindingSource> компоненту вместо непосредственно к источнику данных. Во-вторых, он может управлять коллекцией объектов. Добавление типа в <xref:System.Windows.Forms.BindingSource> создает список этого типа.

Дополнительные сведения о компоненте <xref:System.Windows.Forms.BindingSource> см. в следующих статьях:

- [Компонент BindingSource](/dotnet/framework/winforms/controls/bindingsource-component)

- [Общие сведения о компоненте BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [Архитектура компонента BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[Элемент управления BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) предоставляет пользовательский интерфейс для навигации по данным, отображаемым приложением Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Привязка к данным в элементе управления DataGridView

Для [элемента управления DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms)вся таблица привязана к этому отдельному элементу управления. При перетаскивании **элемента DataGridView** в форму также появляется панель инструментов для просмотра записей (<xref:System.Windows.Forms.BindingNavigator>). [Набор данных](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов. На следующем рисунке также добавлен [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) , так как таблица Customers имеет связь с таблицей Orders. Все эти переменные объявляются в автоматически созданном коде как закрытые члены класса Form. Автоматически созданный код для заполнения **DataGridView** находится в обработчике событий `Form_Load`. Код для сохранения данных для обновления базы данных находится в обработчике событий `Save` для **BindingNavigator**. Этот код можно перемещать или изменять при необходимости.

![GridView с BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Поведение **DataGridView** и **BindingNavigator** можно настроить, щелкнув смарт-тег в правом верхнем углу каждого из них:

![Интеллектуальные Теги навигации и привязки DataGridView](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Если элементы управления, необходимые приложению, недоступны в окне **Источники данных** , можно добавить элементы управления. Дополнительные сведения см. в разделе [Добавление пользовательских элементов управления в окно Источники данных](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Кроме того, можно перетаскивать элементы из окна **Источники данных** на элементы управления, которые уже находятся в форме, чтобы привязать элемент управления к данным. Элементы управления, которые уже привязаны к данным, применяют привязку данных к элементу, который был перемещен в последнее время. Чтобы быть допустимым целевым объектом перетаскивания, элементы управления должны иметь возможность отображения базового типа данных элемента, перетаскиваемого в него, из окна **Источники данных** . Например, недопустимо перетаскивать элемент с типом данных <xref:System.DateTime> в <xref:System.Windows.Forms.CheckBox>, поскольку <xref:System.Windows.Forms.CheckBox> не может отобразить дату.

## <a name="bind-to-data-in-individual-controls"></a>Привязка к данным в отдельных элементах управления

При привязке источника данных к **подробностям**каждый столбец в наборе данных привязывается к отдельному элементу управления.

![Привязать источник данных к подробностям](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Обратите внимание, что на предыдущем рисунке вы перетащили из свойства Orders таблицы Customers, а не из таблицы Orders. При привязке к свойству `Customer.Orders` команды навигации, выполненные в **DataGridView** , немедленно отражаются в элементах управления "подробности". При перетаскивании из таблицы Orders элементы управления все равно будут привязаны к набору данных, но не будут синхронизированы с **DataGridView**.

На следующем рисунке показаны элементы управления, привязанные к данным по умолчанию, которые добавляются в форму после привязки свойства Orders в таблице Customers к **сведениям** в окне **Источники данных** .

![Таблица Orders, привязанная к подробностям](../data-tools/media/raddata-orders-table-bound-to-details.png)

Обратите внимание, что каждый элемент управления имеет смарт-тег. Этот тег включает настройки, применяемые только к этому элементу управления.

## <a name="see-also"></a>См. также:

- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Привязка данных в Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)
