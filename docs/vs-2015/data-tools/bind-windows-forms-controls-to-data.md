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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d2aefe68761d31f87d84c9215a6187c28e7b471b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668994"
---
# <a name="bind-windows-forms-controls-to-data"></a>Привязка элементов управления Windows Forms к данным
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Источники данных можно привязать к элементам управления путем перетаскивания объектов из **источников данных** окна на форму Windows или на существующий элемент управления в форме. Прежде чем перетащить элементы, можно задать тип элемента управления, который вы хотите привязать к. В зависимости от того, самостоятельно, или отдельного столбца выбраны таблицы отображаются разные значения.  Можно также задать пользовательские значения. Для таблицы «Подробности» означает, что каждый столбец привязан к отдельным элементом управления.  
  
 ![Привязка источника данных к DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata привязки источника данных DataGridView")  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>Привязка к данным в элементе управления DataGridView  
 Для DataGridView вся таблица привязан к одного элемента управления. При перетаскивании элемента управления DataGridView на форму, средство удаления для перемещения по записям (<xref:System.Windows.Forms.BindingNavigator>) также отображается. Объект [набора данных](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов. На следующем рисунке TableAdapterManager также добавляется, так как в таблице клиентов имеет отношение к таблице заказов. Эти переменные все объявляются в автоматически сформированном коде как закрытые члены в класс формы. Автоматически созданный код для заполнения DataGridView находится в обработчике событий form_load. Код для сохранения данных для обновления базы данных находится в обработчике событий Save для BindingNavigator. Можно переместить или изменить этот код как требуется.  
  
 ![GridView с BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView с BindingNavigator")  
  
 Можно настроить поведение DataGridView и элемент управления BindingNavigator, щелкнув на смарт-тега в правом верхнем углу каждого из них:  
  
 ![DataGridView и привязка навигатор смарт-теги](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView и привязка навигатор смарт-теги")  
  
 Если элементы управления для приложения требуется не доступные в **источников данных** окно, вы можете добавить элементы управления. Дополнительные сведения см. в разделе [добавлять пользовательские элементы управления окна "Источники данных"](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 Можно также перетаскивать элементы из **источников данных** окна на элементы управления на форму для привязки элемента управления к данным. Элемент управления, который уже привязан к данным содержит данные, восстанавливает привязку к элементу, наиболее недавно перетаскивания его. Допустимые конечные расположения сброса, элементы управления должны быть может отображать базовый тип данных элемента, перетаскиваемого в него из **источников данных** окна. Например, недопустимо перетащите элемент, имеющий тип данных <xref:System.DateTime> на <xref:System.Windows.Forms.CheckBox>, так как <xref:System.Windows.Forms.CheckBox> не способен отображать даты.  
  
## <a name="bind-to--data-in-individual-controls"></a>Привязка к данным в отдельных элементах управления  
 При привязке источника данных к «Подробности», каждый столбец в наборе данных привязан к отдельным элементом управления.  
  
 ![Привязка источника данных к сведения](../data-tools/media/raddata-bind-data-source-to-details.png "raddata привязки источника данных сведения")  
  
> [!IMPORTANT]
>  Обратите внимание, что на предыдущем рисунке, перетащите свойство Orders таблицы клиентов, а не из таблицы Orders. Путем привязки к свойству Customer.Orders команд перехода, внесенные в элемент управления DataGridView, немедленно отражаются в элементы управления сведениями. При перетаскивании из таблицы Orders, элементы управления будет по-прежнему связан с набором данных, но не они не будут синхронизированы с DataGridView.  
  
 На следующем рисунке по умолчанию элементов управления с привязкой к данным, которые добавляются в форму, после привязки свойства заказов в таблице Customers к «Подробности» в **источников данных** окна.  
  
 ![Таблица Orders, привязанный к сведения](../data-tools/media/raddata-orders-table-bound-to-details.png "таблицы Orders raddata привязан к сведения")  
  
 Обратите внимание, что каждый элемент управления имеет смарт-тег. Этот тег включает настройки, относящиеся к этому элементу управления только.  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
