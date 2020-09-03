---
title: Привязка элементов управления Windows Forms к данным | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf93d96594b65b06670567e8c23cd83ccb7f1ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672977"
---
# <a name="bind-windows-forms-controls-to-data"></a>Привязка элементов управления Windows Forms к данным
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Источники данных можно привязать к элементам управления путем перетаскивания объектов из окна **Источники данных** в форму Windows Forms или на существующий элемент управления в форме. Перед перетаскиванием элементов можно задать тип элемента управления, к которому необходимо выполнить привязку. Различные значения отображаются в зависимости от выбора самой таблицы или отдельного столбца.  Можно также задать пользовательские значения. Для таблицы "Details" означает, что каждый столбец привязан к отдельному элементу управления.

 ![Привязка источника данных к DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "Привязка источника данных раддата к DataGridView")

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="bind-to--data-in-a-datagridview-control"></a>Привязка к данным в элементе управления DataGridView
 Для DataGridView вся таблица привязана к одному элементу управления. При перетаскивании элемента DataGridView в форму также появляется панель инструментов для навигации по записям ( <xref:System.Windows.Forms.BindingNavigator> ). [Набор данных](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource> и <xref:System.Windows.Forms.BindingNavigator> отображается в области компонентов. На следующем рисунке также добавлен TableAdapterManager, так как таблица Customers имеет связь с таблицей Orders. Все эти переменные объявляются в автоматически созданном коде как закрытые члены класса Form. Автоматически созданный код для заполнения DataGridView находится в обработчике событий form_load. Код для сохранения данных для обновления базы данных находится в обработчике событий Save для BindingNavigator. Этот код можно перемещать или изменять при необходимости.

 ![GridView с BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "раддата GridView с BindingNavigator")

 Поведение DataGridView и BindingNavigator можно настроить, щелкнув смарт-тег в правом верхнем углу каждого из них:

 ![Интеллектуальные Теги навигации и привязки DataGridView](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "раддата DataGridView и связывание смарт-тегов навигатора")

 Если элементы управления, необходимые приложению, недоступны в окне **Источники данных** , можно добавить элементы управления. Дополнительные сведения см. в разделе [Добавление пользовательских элементов управления в окно Источники данных](../data-tools/add-custom-controls-to-the-data-sources-window.md).

 Кроме того, можно перетаскивать элементы из окна **Источники данных** на элементы управления, которые уже находятся в форме, чтобы привязать элемент управления к данным. Элементы управления, которые уже привязаны к данным, применяют привязку данных к элементу, который был перемещен в последнее время. Чтобы быть допустимым целевым объектом перетаскивания, элементы управления должны иметь возможность отображения базового типа данных элемента, перетаскиваемого в него, из окна **Источники данных** . Например, нельзя перетащить элемент, имеющий тип данных <xref:System.DateTime> <xref:System.Windows.Forms.CheckBox> , на, поскольку не <xref:System.Windows.Forms.CheckBox> может отобразить дату.

## <a name="bind-to--data-in-individual-controls"></a>Привязка к данным в отдельных элементах управления
 При привязке источника данных к «Details» каждый столбец в наборе данных привязывается к отдельному элементу управления.

 ![Привязать источник данных к подробностям](../data-tools/media/raddata-bind-data-source-to-details.png "Источник данных привязки раддата к подробностям")

> [!IMPORTANT]
> Обратите внимание, что на предыдущем рисунке вы перетащили из свойства Orders таблицы Customers, а не из таблицы Orders. При привязке к свойству Customer. Orders команды навигации, выполненные в DataGridView, немедленно отражаются в элементах управления "подробности". При перетаскивании из таблицы Orders элементы управления все равно будут привязаны к набору данных, но не будут синхронизированы с DataGridView.

 На следующем рисунке показаны элементы управления, привязанные к данным по умолчанию, которые добавляются в форму после привязки свойства Orders в таблице Customers к «Details» (сведения) в окне **Источники данных** .

 ![Таблица Orders, привязанная к подробностям](../data-tools/media/raddata-orders-table-bound-to-details.png "Таблица заказов раддата, привязанная к подробностям")

 Обратите внимание, что каждый элемент управления имеет смарт-тег. Этот тег включает настройки, применяемые только к этому элементу управления.

## <a name="see-also"></a>См. также:
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
