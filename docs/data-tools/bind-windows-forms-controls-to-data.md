---
redirect_url: /visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio
ms.openlocfilehash: 5ba8ada294275a99aab27ff9c249d6c3d8e17da3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
Заголовок: «элементы управления Windows Forms привязки к данным | Ms.custom документы Microsoft»:»» ms.date: ms.reviewer «11/04/2016": «» ms.suite:»» ms.tgt_pltfrm:»» ms.topic: «статьи «helpviewer_keywords: 
  - «Отображение данных, элементы управления Windows Forms»
  - «Windows Forms, отображение данных»
  - «Источники данных, отображение»
  - ms.assetid «отображение данных [Windows Forms]»: 0163a34a-38cb-40b9-8f38-3058a90caf21 caps.latest.revision: 28 Автор: ms.author «gewarren»: «gewarren» диспетчера: ghogen ms.technology: «vs data tools»
---
# <a name="bind-windows-forms-controls-to-data"></a>Привязка элементов управления Windows Forms к данным
Источники данных можно привязать к элементам управления путем перетаскивания объектов из **источники данных** окна на форму Windows или на существующий элемент управления в форме. Прежде чем перетащить элементы, можно задать тип элемента управления, который вы хотите привязать к. В зависимости от того, выбрана ли таблица само себя или отдельного столбца отображаются различные значения.  Можно также задать значения по умолчанию. Для таблицы «Подробности» означает, что каждый столбец привязывается к отдельным элементом управления.  

![Привязать источник данных к DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata привязки источника данных DataGridView")  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>Привязка к данным в элементе управления DataGridView  
Для DataGridView вся таблица привязана к одного элемента управления. При перетаскивании элемента управления DataGridView в форму, средство удаления для перемещения по записям (<xref:System.Windows.Forms.BindingNavigator>) также отображается. Объект [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов. На следующем рисунке TableAdapterManager добавляется, так как в таблице Customers имеет отношение к таблице заказов. Эти переменные все объявляются в автоматически сформированном коде как закрытые члены в класс формы. Автоматически созданный код для заполнения DataGridView находится в обработчике событий form_load. Код для сохранения данных для обновления базы данных находится в обработчике событий Save для BindingNavigator. Можно переместить или изменить этот код как требуется.  
  
 ![GridView с BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView с BindingNavigator")  
  
 Можно настроить поведение DataGridView и BindingNavigator, щелкнув на смарт-тега в правом верхнем углу каждого:  
  
 ![DataGridView и привязки навигатор смарт-теги](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView и привязки навигатор смарт-теги")  
  
 Если элементы управления приложения требуется не доступен в **источники данных** окна, можно добавить элементы управления. Дополнительные сведения см. в разделе [добавить пользовательские элементы управления в окно источников данных](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 Можно также перетаскивать элементы из **источники данных** окна на элементы управления на форму для привязки элемента управления к данным. Элемент управления, который уже привязан к данным содержит данные, восстанавливает привязку к элементу, недавно перетаскивания его. Допустимые целевые объекты перетаскивания, элементы управления должны быть рисунках базовый тип данных элемента, перетаскиваемые на него из **источники данных** окна. Например, не допускается перетащите элемент, имеющий тип данных <xref:System.DateTime> на <xref:System.Windows.Forms.CheckBox>, так как <xref:System.Windows.Forms.CheckBox> не может отображать даты.  
  
## <a name="bind-to--data-in-individual-controls"></a>Привязка к данным в отдельных элементах управления  
 При привязке источника данных «Подробности», каждый столбец в наборе данных привязан к отдельным элементом управления.  
  
 ![Привязать источник данных к сведения](../data-tools/media/raddata-bind-data-source-to-details.png "raddata привязки источника данных подробные сведения")  
  
> [!IMPORTANT]
>  Обратите внимание, что на предыдущем рисунке, перетащите из таблицы Customers, не из таблицы Orders свойства заказов. Путем привязки к свойству Customer.Orders команд перехода, внесенные в элемент управления DataGridView, немедленно отражаются в элементы управления сведениями. При перетаскивании таблицы Заказы, элементы управления по-прежнему будет привязываться к набору данных, но не они не будут синхронизированы с DataGridView.  
  
 На следующей иллюстрации по умолчанию элементы управления с привязкой к данным, которые добавляются в форму после свойство заказов в таблице Customers привязывается к «Подробности» в **источники данных** окна.  
  
 ![Таблица Orders, привязанный к сведения](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata таблицу Orders, привязанный к подробные сведения")  
  
 Обратите внимание, что каждый элемент управления имеет смарт-тега. Этот тег включает настройки, относящиеся к этому элементу управления только.  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)