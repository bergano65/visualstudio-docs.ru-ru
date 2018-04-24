---
title: Привязка объектов в Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5b515a802c4b82bb3b1400f5ea88720242b80aa9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="bind-objects-in-visual-studio"></a>Привязка объектов в Visual Studio
Visual Studio предоставляет средства разработки для работы с пользовательскими объектами в качестве источника данных в приложении. Если вы хотите сохранить данные из базы данных в объект, который можно привязать к элементам управления пользовательского интерфейса, рекомендуется использовать Entity Framework для создания класса или классов. Платформа Entity Framework автоматически создает всего стандартного отслеживания изменений кода, это означает, что все изменения локальных объектов, автоматически сохраняется в базу данных при вызове метода AcceptChanges DbSet объекта. Дополнительные сведения см. в разделе [документации по Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
>  Подходы к объекта привязки в этой статье следует рассматривать, только если приложение уже основана на наборы данных. Эти подходы можно также в том случае, если вы уже знакомы с наборами данных и данные, которые будет обрабатывать табличной и не слишком сложная или слишком велик. Пример еще проще, связанных с загрузкой данных непосредственно в объекты с помощью объекта DataReader и вручную обновить пользовательский Интерфейс без привязки к данным, в разделе [Создание простых данных приложения с помощью ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Требования к объекту
 Единственное требование для пользовательских объектов для работы с данными средства разработки в Visual Studio заключается в том, что объекту требуется по крайней мере одно общее свойство.

 Как правило пользовательские объекты не требуют все интерфейсы, определяемые конструкторы атрибутов или в качестве источника данных для приложения. Тем не менее если вы хотите перетащите объект из **источники данных** окна в рабочую область конструирования для создания элемента управления с привязкой к данным и, если объект реализует <xref:System.ComponentModel.ITypedList> или <xref:System.ComponentModel.IListSource> интерфейс, объект должен иметь значение по умолчанию конструктор. В противном случае Visual Studio не удается создать экземпляр объекта источника данных, и он выводит сообщение об ошибке при перетаскивании элемента в область конструктора.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Примеры использования пользовательских объектов в качестве источников данных
 Хотя существует множество способов реализовать логику приложения при работе с объектами в качестве источника данных, для SQL базы данных существует, несколько стандартных операций, которые можно упростить с помощью объектов TableAdapter, созданный средой Visual Studio. Эта страница содержит описание реализации этих стандартных процессов с помощью TableAdapters.It не предназначен в качестве руководства по созданию пользовательских объектов. Например обычно выполняются следующие стандартные операции независимо от конкретной реализации объектов или логики приложения.

-   Загрузка данных в объекты (обычно из базы данных).

-   Создание типизированных коллекций объектов.

-   Объекты для добавления и удаления объектов из коллекции.

-   Отображение данных объектов для пользователей на форме.

-   Изменение или редактирование данных в объект.

-   Сохранение данных из объектов в базе данных.

### <a name="load-data-into-objects"></a>Загрузка данных в объекты
 В этом примере загрузка данных в объекты с помощью адаптера таблицы. По умолчанию адаптеры таблиц создаются с использованием двух типов методов для выборки данных из базы данных и заполнения таблиц данных.

-   `TableAdapter.Fill` Метод заполняет существующие таблицы данных возвращаемыми данными.

-   `TableAdapter.GetData` Метод возвращает новую таблицу данных заполняются данными.

 Самый простой способ загрузить пользовательские объекты с данными является вызов `TableAdapter.GetData` метод, цикл по коллекции строк в таблице возвращаемых данных и заполнение каждого объекта со значениями в каждой строке. Можно создать `GetData` метод, возвращающий заполненные таблицы данных для любого запроса, добавленного в адаптер таблицы.

> [!NOTE]
>  Visual Studio именует запросы адаптера таблиц `Fill` и `GetData` по умолчанию, но эти имена можно изменить на любое действительное имя метода.

 Приведенный ниже показано, как в цикле по строкам в таблице данных и заполнить объект с данными:

 [!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Создайте коллекцию типизированных объектов
 Можно создать классы коллекций для объектов или использовать типизированные коллекции, автоматически предоставляемые [компонент BindingSource](/dotnet/framework/winforms/controls/bindingsource-component).

 Если вы создаете настраиваемый класс коллекции для объектов, мы советуем использовать наследование от <xref:System.ComponentModel.BindingList%601>. Этот универсальный класс предоставляет функциональные возможности для администрирования коллекции, а также возможность вызывать события, отправлять уведомления в инфраструктуру привязки данных в Windows Forms.

 Коллекция автоматически создается в <xref:System.Windows.Forms.BindingSource> использует <xref:System.ComponentModel.BindingList%601> для своей типизированной коллекции. Если приложение не требует дополнительных функций, то можно поддерживать в коллекцию в <xref:System.Windows.Forms.BindingSource>. Дополнительные сведения см. в разделе <xref:System.Windows.Forms.BindingSource.List%2A> свойство <xref:System.Windows.Forms.BindingSource> класса.

> [!NOTE]
>  Если ваша коллекция требуются функциональные возможности, не предоставляемые базовую реализацию <xref:System.ComponentModel.BindingList%601>, следует создать пользовательскую коллекцию, можно добавить в класс при необходимости.

 Ниже показано, как создать класс для строго типизированной коллекции `Order` объектов:

 [!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Добавить объекты в коллекцию
 Добавить объекты в коллекцию, вызвав `Add` метод вашего класса пользовательской коллекции или <xref:System.Windows.Forms.BindingSource>.


> [!NOTE]
>  `Add` Метод автоматически предоставляется для пользовательской коллекции при наследовании от <xref:System.ComponentModel.BindingList%601>.

 Следующий код показывает, как добавлять объекты в типизированную коллекцию в <xref:System.Windows.Forms.BindingSource>:

 [!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

 Следующий код показывает, как добавлять объекты в типизированную коллекцию, который наследует от <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
>  В этом примере `Orders` коллекции — это свойство `Customer` объекта.

 [!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Удаление объектов из коллекции
 Удалить объекты из коллекции путем вызова `Remove` или `RemoveAt` метод вашего класса пользовательской коллекции или <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
>  `Remove` И `RemoveAt` автоматически предоставляются методы для пользовательской коллекции при наследовании от <xref:System.ComponentModel.BindingList%601>.

 Ниже показано, как для поиска и удаления объектов из типизированных коллекций, в <xref:System.Windows.Forms.BindingSource> с <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> метод:

 [!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Отображать данные объекта для пользователей
 Для отображения данных объектов для пользователей, создайте источник данных объекта с помощью **конфигурации источника данных** мастера, а затем перетащите весь объект или отдельные свойства на форму из **источники данных**окна.

### <a name="modify-the-data-in-objects"></a>Изменение данных в объектах
 Чтобы изменить данные в пользовательских объектах, которые привязаны к элементам управления Windows Forms, просто измените данные в связанном элементе управления (или непосредственно в свойствах объекта). Архитектура привязки данных обновляет данные в объекте.

 Если приложение требует отслеживания изменений и отката произошедших изменений к исходным значениям, необходимо реализовать эту функциональность в объектной модели. Примеры как таблицы данных хранить список предложенных изменений см. в разделе <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, и <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="save-data-in-objects-back-to-the-database"></a>Сохранение данных в объекты в базе данных
 Сохраните данные в базе данных путем передачи значений из объекта в методы DBDirect адаптера таблицы.

 Visual Studio создает DBDirect-методы, которые могут быть выполнены непосредственно с базой данных. Эти методы не используют объекты DataSet или DataTable.

|Метод DBDirect адаптера таблицы|Описание|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Добавляет новые записи в базу данных, что позволяет передавать значения отдельных столбцов в качестве параметров метода.|
|`TableAdapter.Update`|Обновляет существующие записи в базе данных. Метод Update принимает исходные и новые значения столбцов в качестве параметров метода. Исходные значения используются для обнаружения исходной записи, а новые значения используются для обновления этой записи.<br /><br /> `TableAdapter.Update` Метод также используется для согласования изменений в наборе данных обратно в базу данных, используя <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, или массив <xref:System.Data.DataRow>как параметры метода.|
|`TableAdapter.Delete`|Удаляет существующие записи из базы данных, основанный на исходных значениях столбцов, переданных в качестве параметров метода.|

 Чтобы сохранить данные из коллекции объектов, цикл по коллекции объектов (например, с помощью цикла для далее). Отправьте значения для каждого объекта базы данных с помощью методов DBDirect адаптера таблицы.

 В следующем примере показано, как использовать `TableAdapter.Insert` DBDirect метода для добавления нового клиента непосредственно в базе данных:

 [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>См. также

- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)