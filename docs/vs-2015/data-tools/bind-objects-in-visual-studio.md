---
title: Привязка объектов
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
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 12cbeca740fd81292109183468a304fc2d3da30c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439493"
---
# <a name="bind-objects-in-visual-studio"></a>Связывание объектов в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio предоставляет средства разработки для работы с пользовательскими объектами в качестве источника данных в приложении. Если вы хотите сохранять данные из базы данных в объект, который можно привязать к элементам управления пользовательского интерфейса, рекомендуется использовать Entity Framework для создания класса или классов. Сущность Frameworkautogenerates весь отслеживания изменений код шаблона, это означает, что любые изменения локальных объектов автоматически сохраняются в базу данных при вызове AcceptChanges DbSet объекта.    Дополнительные сведения см. в разделе [документация по Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Подходы к привязке объектов в этой статье должен рассматриваться только в тех случаях, если приложение уже основана на наборы данных. Эти подходы можно использовать также в том случае, если вы уже знакомы с наборами данных и данные, которые планируется обработка табличной и не слишком сложным или слишком большое. Пример еще проще, связанных с загрузкой данных непосредственно в объекты с помощью объекта DataReader и обновление пользовательского интерфейса без привязки данных, вручную см. в разделе [Создание простых данных приложения с помощью ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Требования к объекту
 Единственным требованием для пользовательских объектов для работы с данными, средства разработки в Visual Studio является то, что объекту требуется по крайней мере одно открытое свойство.

 Как правило пользовательские объекты не требуют все определенные интерфейсы, конструкторы или атрибуты в качестве источника данных для приложения. Тем не менее если вы хотите перетащите объект из **источников данных** окно в рабочую область конструирования для создания элемента управления с привязкой данных, и если объект реализует <xref:System.ComponentModel.ITypedList> или <xref:System.ComponentModel.IListSource> интерфейс, объект должен иметь значение по умолчанию конструктор. В противном случае Visual Studio не удается создать экземпляр объекта источника данных, и он отображает сообщение об ошибке при перетаскивании элемента в область конструктора.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Примеры использования пользовательских объектов в качестве источников данных
 Хотя существует множество способов реализовать логику приложения при работе с объектами в качестве источника данных, для SQL базы данных существует являются несколько стандартных операций, которые можно упростить с помощью Visual Studio создаваемых объектов TableAdapter. Этой странице объясняется, как реализовать эти стандартные процессы с помощью TableAdapters.It не предназначен для справки по созданию пользовательских объектов. Например обычно выполняют следующие стандартные операции независимо от конкретной реализации объектов или логикой приложения.

- Загрузка данных в объекты (обычно из базы данных).

- Создание типизированных коллекций объектов.

- Добавление объектов и их удаление из коллекции.

- Отображение данных объекта для пользователей в форме.

- Изменение/редактирование данных в объекте.

- Сохранение данных из объектов в базе данных.

> [!NOTE]
> Чтобы лучше понять и предоставить контекст для примеров на этой странице, рекомендуем выполнить следующие действия. [Пошаговое руководство: Подключение к данным в объектах (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05). Для этого пошагового руководства создаются объекты, обсуждаемые здесь.

### <a name="loaddata-into-objects"></a>LoadData в объекты
 Например загрузка данных в объекты с помощью адаптера таблицы. По умолчанию адаптеры таблиц создаются с использованием двух типов, методов для выборки данных из базы данных и заполнения таблиц данных.

- `TableAdapter.Fill` Метод заполняет существующую таблицу данных, возвращаемыми данными.

- `TableAdapter.GetData` Метод возвращает новую таблицу данных, заполненную данными.

  Самый простой способ загрузить пользовательские объекты с данными является вызов `TableAdapter.GetData` метод, циклический перебор коллекции строк в таблице возвращаемых данных и заполнения каждого объекта со значениями в каждой строке. Можно создать `GetData` метод, возвращающий заполненные таблицы данных для любого запроса, добавленного в адаптер таблицы.

> [!NOTE]
> Visual Studio Присваивает запросы адаптера таблиц `Fill` и `GetData` по умолчанию, но эти имена можно изменить для любого допустимого имени метода.

 В следующем примере показано, как цикле по строкам в таблице данных и заполнение объекта с данными:

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>Создайте коллекцию типизированных объектов
 Можно создать классы коллекций для объектов или использовать типизированные коллекции, автоматически предоставляемые [компонент BindingSource](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9).

 Когда вы создаете пользовательский класс коллекции для объектов, мы рекомендуем, что выполняется наследование от <xref:System.ComponentModel.BindingList%601>. Этот общий класс предоставляет функциональные возможности для администрирования коллекции, а также возможность вызывать события, отправлять уведомления в инфраструктуру привязки данных в Windows Forms.

 Коллекция автоматически создается в <xref:System.Windows.Forms.BindingSource> использует <xref:System.ComponentModel.BindingList%601> для его типизированной коллекции. Если приложения не требуются дополнительные функции, то можно поддерживать в коллекцию в <xref:System.Windows.Forms.BindingSource>. Дополнительные сведения см. в разделе <xref:System.Windows.Forms.BindingSource.List%2A> свойство <xref:System.Windows.Forms.BindingSource> класса.

> [!NOTE]
> Если ваша коллекция требуются функции, не предоставляется базовая реализация <xref:System.ComponentModel.BindingList%601>, следует создать пользовательскую коллекцию, при необходимости можно добавить к классу.

 Ниже показано, как создать класс для строго типизированной коллекции `Order` объектов:

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>Addobjects в коллекцию
 Добавление объектов в коллекцию путем вызова `Add` метод класса пользовательской коллекции или из <xref:System.Windows.Forms.BindingSource>.

 Пример добавления в коллекцию с помощью <xref:System.Windows.Forms.BindingSource>, см. в разделе `LoadCustomers` метод в [Пошаговое руководство: Подключение к данным в объектах (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

 Пример добавления объектов в пользовательскую коллекцию, см. в разделе `LoadOrders` метод в [Пошаговое руководство: Подключение к данным в объектах (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

> [!NOTE]
> `Add` Метод автоматически предоставляется для пользовательской коллекции при наследовании от класса <xref:System.ComponentModel.BindingList%601>.

 Следующий код демонстрирует добавление объектов в типизированную коллекцию в <xref:System.Windows.Forms.BindingSource>:

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 Следующий код демонстрирует добавление объектов в типизированную коллекцию, который наследует от <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
> В этом примере `Orders` коллекции — это свойство `Customer` объекта.

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>Removeobjects из коллекции
 Удаление объектов из коллекции путем вызова `Remove` или `RemoveAt` метод класса пользовательской коллекции или из <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> `Remove` И `RemoveAt` автоматически предоставляются методы для пользовательской коллекции при наследовании от класса <xref:System.ComponentModel.BindingList%601>.

 Приведенный ниже показано, как найти и удалить объекты из коллекции типизированных в <xref:System.Windows.Forms.BindingSource> с <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> метод:

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>Данные DisplayObject для пользователей
 Для отображения данных объектов для пользователей, создайте источник данных объекта с помощью **конфигурации источника данных** мастера, а затем перетащите на форму из весь объект или отдельные свойства **источников данных**окно.

### <a name="modify-the-data-in-objects"></a>Изменения данных в объекты
 Чтобы изменить данные в пользовательских объектах, которые привязаны к элементам управления Windows Forms, просто измените данные в привязанном элементе управления (или непосредственно в свойствах объекта). Архитектура привязки данных обновляет данные в объекте.

 Если приложению требуется отслеживание изменений и отката произошедших изменений к исходным значениям, необходимо реализовать эту функцию в объектной модели. Примеры как таблицы данных хранить список предлагаемых изменений, см. в разделе <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, и <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="savedata-in-objects-back-to-the-database"></a>SaveData в объектах в базе данных
 Сохраните данные в базе данных путем передачи значения из объекта методы DBDirect адаптера таблицы.

 Visual Studio создает DBDirect-методы, которые могут быть выполнены непосредственно в базе данных. Эти методы не требуют объекты DataSet или DataTable.

|Метод TableAdapter DBDirect|Описание|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Добавляет новые записи в базу данных, позволяя передавать значения отдельных столбцов в качестве параметров метода.|
|`TableAdapter.Update`|Обновляет существующие записи в базе данных. Метод Update принимает исходные и новые значения столбцов в качестве параметров метода. Исходные значения используются для обнаружения исходной записи, а новые значения используются для обновления этой записи.<br /><br /> `TableAdapter.Update` Метод также используется для согласования изменений в наборе данных в базе данных, используя <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, или массив <xref:System.Data.DataRow>s как параметры метода.|
|`TableAdapter.Delete`|Удаляет существующие записи из базы данных, основанный на исходных значениях столбца, переданный в качестве параметров метода.|

 Для сохранения данных из коллекции объектов, циклический перебор коллекции объектов (например, с помощью для следующего цикла). Отправки значений для каждого объекта в базу данных с помощью методов DBDirect адаптера таблицы.

 В следующем примере показано, как использовать `TableAdapter.Insert` DBDirect метод для добавления нового клиента непосредственно в базе данных:

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>См. также
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
