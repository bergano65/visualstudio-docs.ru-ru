---
title: 'Walkthrough: Creating an N-Tier Data Application | Microsoft Docs'
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
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 51
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bd77006eda03b716e3c54c0b5b52ac633a383377
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299595"
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Пошаговое руководство. Создание многоуровневого приложения для работы с данными
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N-tier* data applications are applications that access data and are separated into multiple logical layers, or *tiers*. Разделение компонентов приложения на несколько отдельных уровней повышает удобство обслуживания и масштабируемость приложения. Это обеспечивается за счет упрощения внедрения новых технологий, которые можно применить к отдельному уровню без пересмотра всего решения. N-уровневая архитектура включает в себя уровень представления, средний уровень и уровень данных. Средний уровень обычно содержит слой доступа к данным, слой бизнес-логики и общие компоненты, такие как аутентификация и проверка. Уровень данных содержит реляционную базу данных. N-уровневые приложения обычно хранят конфиденциальную информацию на слое доступа к данным среднего уровня, чтобы обеспечить изоляцию от конечных пользователей, работающих с уровнем представления. For more information, see [N-Tier Data Applications Overview](../data-tools/n-tier-data-applications-overview.md).

 Один из способов разделения разных уровней в n-уровневом приложении заключается в создании отдельных проектов для каждого уровня, который требуется включить в приложение. Типизированные наборы данных содержат свойство `DataSet Project`, определяющее, в какие проекты следует передать созданный набор данных и код `TableAdapter`.

 В данном пошаговом руководстве демонстрируется, как разделить набор данных и код `TableAdapter` по отдельным проектам библиотеки классов с помощью **конструктора наборов данных**. After you separate the dataset and TableAdapter code, you will create a [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) service to call into the data access tier. Наконец, вы создадите приложение Windows Forms в качестве уровня представления. Этот уровень осуществляет доступ к данным из службы данных.

 В этом пошаговом руководстве выполняются следующие задачи.

- Создание нового n-уровневого решения, содержащего несколько проектов.

- Добавление в n-уровневое решение двух проектов библиотеки классов.

- Создание типизированного набора данных с помощью **мастера настройки источника данных**.

- Separate the generated [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) and dataset code into discrete projects.

- Создание службы WCF для вызова уровня доступа к данным.

- Создание функций в службе для извлечения данных из уровня доступа к данным.

- Создание приложения Windows Forms для использования в качестве уровня представления.

- Создание элементов управления Windows Forms с привязкой к источнику данных.

- Написание кода для заполнения таблиц данных.

  ![link to video](../data-tools/media/playvideo.gif "PlayVideo") For a video version of this topic, see [Video How to: Creating an N-Tier Data Application](https://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Необходимые компоненты
 Для выполнения данного пошагового руководства требуется:

- Доступ к примеру базы данных "Борей".

## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Создание N-уровневого решения и библиотеки классов для хранения набора данных (DataEntityTier)
 Первым шагом данного руководства является создание решения и двух проектов библиотеки классов. Первая библиотека классов будет содержать набор данных (сформированный класс типизированного набора данных и таблицы данных, которые будут содержать данные приложения). Этот проект используется в качестве слоя сущностей данных приложения и обычно находится в среднем уровне. The Dataset Designer is used to create the initial dataset and automatically separate the code into the two class libraries.

> [!NOTE]
> Обязательно присвойте проекту и решению правильные имена перед нажатием кнопки **ОК**. Это облегчит выполнение данного пошагового руководства.

#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Создание n-уровневого решения и библиотеки классов DataEntityTier

1. From the **File** menu, create a new project.

    > [!NOTE]
    > The **Dataset Designer** is supported in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] and C# projects. Создайте новый проект на одном из этих языков.

2. In the **New Project** dialog box, in the **Project types** pane, click **Windows**.

3. Click the **Class Library** template.

4. Присвойте проекту имя **DataEntityTier**.

5. Name the solution **NTierWalkthrough**.

6. Нажмите кнопку **ОК**.

     Создается решение NTierWalkthrough, содержащее проект DataEntityTier, которое добавляется в **Обозреватель решений**.

## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Создание библиотеки классов для хранения адаптеров таблицы (DataAccessTier)
 Следующий наг после создания проекта DataEntityTier заключается в создании другого проекта библиотеки классов. This project will hold the generated `TableAdapter`s and is called the *data access tier* of the application. Уровень доступа к данным содержит информацию, необходимую для подключения к базе данных, и обычно находится на среднем уровне.

#### <a name="to-create-the-new-class-library-for-the-tableadapters"></a>Создание новой библиотеки классов для адаптеров таблиц

1. From the **File** menu, add a new project to the NTierWalkthrough solution.

2. In the **New Project** dialog box, in the **Templates** pane, click **Class Library**.

3. Name the project **DataAccessTier** and click **OK**.

     Создается проект DataAccessTier, который добавляется в решение NTierWalkthrough.

## <a name="creating-the-dataset"></a>Создание набора данных
 Следующим шагом является создание типизированного набора данных. Типизированные наборы данных создаются с классом набора данных (включая классы таблиц данных) и классами `TableAdapter` в одном проекте. (All classes are generated into a single file.) When you separate the dataset and `TableAdapter`s into different projects, it is the dataset class that is moved to the other project, leaving the `TableAdapter` classes in the original project. Таким образом, создайте набор данных в проекте, который в конечном итоге будет содержать `TableAdapter` (проект DataAccessTier). You will create the dataset by using the **Data Source Configuration Wizard**.

> [!NOTE]
> Для создания подключения необходимо иметь доступ к учебной базе данных "Борей".

#### <a name="to-create-the-dataset"></a>Создание набора данных

1. Click DataAccessTier in **Solution Explorer**.

2. В меню **Данные** выберите команду **Показать источники данных**.

3. In the **Data Sources** window, click **Add New Data Source** to start the **Data Source Configuration Wizard**.

4. On the **Choose a Data Source Type** page, click **Database** and then click **Next**.

5. На странице **Выбор подключения к базе данных** выполните одно из следующих действий:

     Если подключение к учебной базе данных "Борей" доступно в раскрывающемся списке, то выберите его.

     \- или -

     Click **New Connection** to open the **Add Connection** dialog box.

6. Если базе данных требуется пароль, выберите параметр для включения конфиденциальных данных и щелкните **Далее**.

    > [!NOTE]
    > Если вы выбрали файл локальной базы данных (вместо подключения к SQL Server), может отображаться запрос о том, требуется ли включить этот файл в проект. Click **Yes** to add the database file to the project.

7. Click **Next** on the **Save the Connection String to the Application Configuration File** page.

8. Разверните узел **Таблицы** на странице **Выбор объектов базы данных** .

9. Click the check boxes for the **Customers** and **Orders** tables, and then click **Finish**.

     NorthwindDataSet добавляется в проект DataAccessTier и отображается в окне **Источники данных**.

## <a name="separating-the-tableadapters-from-the-dataset"></a>Отделение адаптеров таблиц от набора данных
 После создания набора данных отделите сформированный класс набора данных от адаптеров таблицы. Для этого задайте для свойства **Проект DataSet** имя проекта, в котором требуется хранить отделенный класс набора данных.

#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Порядок отделения адаптеров таблиц от набора данных

1. Дважды щелкните **NorthwindDataSet.xsd** в **обозревателе решений**, чтобы открыть набор данных в **конструкторе наборов данных**.

2. Щелкните пустое пространство в конструкторе.

3. Найдите узел **Проект DataSet** в окне **Свойства**.

4. In the **DataSet Project** list, click **DataEntityTier**.

5. В меню **Сборка** выберите **Собрать решение**.

   Набор данных и адаптеры таблицы делятся на два проекта библиотеки классов. Проект, который изначально содержал весь набор данных (DataAccessTier), теперь содержит только адаптеры таблицы. The project designated in the **DataSet Project** property (DataEntityTier) contains the typed dataset: NorthwindDataSet.Dataset.Designer.vb (or NorthwindDataSet.Dataset.Designer.cs).

> [!NOTE]
> При разделении наборов данных и адаптеров таблиц (посредством установки свойства **Проект DataSet**) существующие разделяемые классы наборов данных в проекте не перемещаются автоматически. Их необходимо переместить в проект набора данных вручную.

## <a name="creating-a-new-service-application"></a>Создание нового приложения службы
 Поскольку это пошаговое руководство демонстрирует, как получить доступ к уровню доступа к данным с помощью службы WCF, создайте новое приложение службы WCF.

#### <a name="to-create-a-new-wcf-service-application"></a>Создание нового приложения службы WCF

1. From the **File** menu, add a new project to the NTierWalkthrough solution.

2. In the **New Project** dialog box, in the **Project types** pane, click **WCF**. In the **Templates** pane, click **WCF Service Library**.

3. Name the project **DataService** and click **OK**.

     Создается проект DataService, который добавляется в решение NTierWalkthrough.

## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Создание методов на уровне доступа к данным для возврата данных о клиентах и заказах
 Служба данных должна вызывать два метода на уровне доступа к данным: GetCustomers и GetOrders. Эти методы возвращают таблицы клиентов и заказов базы данных "Борей". Создайте методы GetCustomers и GetOrders в проекте DataAccessTier.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Создание метода на уровне доступа к данным, возвращающего таблицу клиентов

1. In **Solution Explorer**, double-click NorthwindDataset.xsd to open the dataset in the Dataset Designer.

2. Right-click CustomersTableAdapter and click **Add Query** to edit the Tableadapter.

3. На странице **Выбор типа команды** оставьте значение по умолчанию для параметра **Использовать инструкции SQL** и нажмите кнопку **Далее**.

4. На странице **Выбор типа запроса** оставьте значение по умолчанию для параметра **Инструкция SELECT, возвращающая строки** и нажмите кнопку **Далее**.

5. На странице **Укажите SQL-инструкцию SELECT** оставьте запрос по умолчанию и нажмите кнопку **Далее**.

6. На странице **Выбор методов для автоматического создания** введите **GetCustomers** для параметра **Имя метода** в разделе **Вернуть таблицу данных (DataTable)** .

7. Нажмите кнопку **Готово**.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Создание метода на уровне доступа к данным, возвращающего таблицу заказов

1. Right-click OrdersTableAdapter and click **Add Query**.

2. На странице **Выбор типа команды** оставьте значение по умолчанию для параметра **Использовать инструкции SQL** и нажмите кнопку **Далее**.

3. На странице **Выбор типа запроса** оставьте значение по умолчанию для параметра **Инструкция SELECT, возвращающая строки** и нажмите кнопку **Далее**.

4. На странице **Укажите SQL-инструкцию SELECT** оставьте запрос по умолчанию и нажмите кнопку **Далее**.

5. На странице **Выбор методов для автоматического создания** введите **GetOrders** для параметра **Имя метода** в разделе **Вернуть таблицу данных (DataTable)** .

6. Нажмите кнопку **Готово**.

7. В меню **Сборка** выберите **Собрать решение**.

## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Добавление в службу данных ссылки на уровни сущностей данных и доступа к данным
 Поскольку службе данных необходима информация из набора данных и адаптеров таблицы, добавьте ссылки на проекты DataEntityTier и DataAccessTier.

#### <a name="to-add-references-to-the-data-service"></a>Добавление ссылок в службу данных

1. Right-click DataService in **Solution Explorer** and click **Add Reference**.

2. Откройте вкладку **Проекты** в диалоговом окне **Добавление ссылки**.

3. Выберите проекты **DataAccessTier** и **DataEntityTier**.

4. Нажмите кнопку **ОК**.

## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Добавление функций в службу для вызова методов GetCustomers и GetOrders на уровне доступа к данным
 Теперь, когда уровень доступа к данным содержит методы для возврата данных, создайте в службе данных методы для вызова методов на уровне доступа к данным.

> [!NOTE]
> Для проектов C# необходимо добавить ссылку на сборку `System.Data.DataSetExtensions`, чтобы следующий код прошел компиляцию.

#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Создание функций GetCustomers и GetOrders в службе данных

1. In the **DataService** project, double-click IService1.vb or IService1.cs.

2. Добавьте следующий код под комментарием **Добавьте здесь операции служб**:

    ```vb
    <OperationContract()> _
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable

    <OperationContract()> _
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable
    ```

    ```csharp
    [OperationContract]
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();

    [OperationContract]
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();

    ```

3. В проекте DataService дважды щелкните Service1.vb (или Service1.cs).

4. Добавьте следующий код в класс Service1:

    ```vb
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
        Return CustomersTableAdapter1.GetCustomers()
    End Function

    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
        Return OrdersTableAdapter1.GetOrders()
    End Function
    ```

    ```csharp
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
             CustomersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();
        return CustomersTableAdapter1.GetCustomers();

    }
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
             OrdersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();
        return OrdersTableAdapter1.GetOrders();

    }
    ```

5. В меню **Сборка** выберите **Собрать решение**.

## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Создание уровня представления для отображения данных из службы данных
 Теперь, когда решение содержит службу данных с методами для выполнения вызовов на уровне доступа к данным, создайте еще один проект, который будет вызывать службу данных и представлять данные пользователям. В рамках данного руководства создайте приложение Windows Forms — это уровень представления n-уровневого приложения.

#### <a name="to-create-the-presentation-tier-project"></a>Создание проекта уровня представления

1. From the **File** menu, add a new project to the NTierWalkthrough solution.

2. In the **New Project** dialog box, in the **Project types** pane, click **Windows**. Выберите **Приложение Windows Forms** в области **Шаблоны**.

3. Присвойте проекту имя **PresentationTier** и нажмите кнопку **ОК**.

4. Создается проект PresentationTier, который добавляется в решение NTierWalkthrough.

## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Настройка проекта PresentationTier в качестве запускаемого
 Поскольку уровень представления фактически является клиентским приложением, используемым для представления данных и взаимодействия с ними, вам следует настроить проект PresentationTier в качестве запускаемого проекта.

#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Порядок настройки нового проекта уровня представления в качестве запускаемого

- В **обозревателе решений** щелкните правой кнопкой мыши **PresentationTier** и выберите команду **Назначить запускаемым проектом**.

## <a name="adding-references-to-the-presentation-tier"></a>Добавление ссылок на уровень представления
 Клиентскому приложению PresentationTier требуется ссылка на службу в службе данных для получения доступа к методам в этой службе. Кроме того, требуется ссылка на набор данных для обеспечения совместного использования типов службой WCF. До включения совместного использования типов с помощью службы данных код, добавленный в разделяемый класс наборов данных, будет недоступен для уровня представления. Поскольку вы обычно добавляете код, например код проверки, в события таблицы данных, изменяющие строку и столбец, вполне вероятно, что вы хотите получить доступ к этому коду из клиента.

#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Добавление ссылки на уровень представления

1. In **Solution Explorer**, right-click PresentationTier and click **Add Reference**.

2. In the **Add Reference** dialog box, click the **Projects** tab.

3. Select **DataEntityTier** and click **OK**.

#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Добавление ссылки на службу на уровень представления

1. In **Solution Explorer**, right-click PresentationTier and click **Add Service Reference**.

2. В диалоговом окне **Добавление ссылки на службу** щелкните элемент **Найти**.

3. Select **Service1** and click **OK**.

    > [!NOTE]
    > Если на текущем компьютере имеется несколько служб, выберите службу, созданную ранее в рамках работы с этим руководством (эта служба содержит методы GetCustomers и GetOrders).

## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Добавление элементов DataGridView в форму для отображения данных, возвращаемых службой данных
 После добавления ссылки на службу в службу данных окно **Источники данных** автоматически заполняется возвращенными службой данными.

#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Создание двух элементов DataGridView с привязкой к данным на форме

1. In **Solution Explorer**, select the PresentationTier project.

2. В окне **Источники данных** разверните **NorthwindDataSet** и найдите узел **Customers**.

3. Перетащите узел **Customers** на форму Form1.

4. В окне **Источники данных** разверните узел **Customers** и найдите связанный узел **Orders** (узел **Orders** вложен в узел **Customers**).

5. Перетащите связанный узел **Orders** на форму Form1.

6. Создайте обработчик событий `Form1_Load`, дважды щелкнув пустую область на форме.

7. Добавьте следующий код в обработчик событий `Form1_Load`.

    ```vb
    Dim DataSvc As New ServiceReference1.Service1Client
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)
    ```

    ```csharp
    ServiceReference1.Service1Client DataSvc =
        new ServiceReference1.Service1Client();
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());

    ```

## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Увеличение максимально допустимого размера сообщения для службы
 Поскольку служба возвращает данные из таблиц "Клиенты" и "Заказы", значение по умолчанию для maxReceivedMessageSize слишком мало для хранения данных, поэтому его следует увеличить. В этом пошаговом руководстве вы измените это значение на 6553600. Вы измените это значение в клиенте, после чего будет автоматически обновлена ссылка на службу.

> [!NOTE]
> Меньший размер по умолчанию призван ограничить уязвимость для атак типа "отказ в обслуживании" (DoS). Для получения дополнительной информации см. <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Увеличение значения maxReceivedMessageSize

1. In **Solution Explorer**, double-click the app.config file in the PresentationTier project.

2. Найдите атрибут размера **maxReceivedMessage** и измените его значение на `6553600`.

## <a name="testing-the-application"></a>Тестирование приложения
 Запустите приложение. Данные извлекаются из службы данных и отображаются на форме.

#### <a name="to-test-the-application"></a>Тестирование приложения

1. Нажмите клавишу F5.

2. Данные из таблиц клиентов и заказов извлекаются из службы данных и отображаются на форме.

## <a name="next-steps"></a>Следующие шаги
 В зависимости от требований приложения существуют несколько шагов, которые, возможно, потребуется выполнить после сохранения связанных данных в приложении Windows. Ниже приводится перечень рекомендаций, позволяющих улучшить данное приложение.

- Добавьте проверку в набор данных. For information, see [Walkthrough: Adding Validation to an N-Tier Data Application](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265).

- Добавьте в службу дополнительные методы для обновления данных в базе данных.

## <a name="see-also"></a>См. также раздел
 [Work with datasets in n-tier applications](../data-tools/work-with-datasets-in-n-tier-applications.md) [Hierarchical update](../data-tools/hierarchical-update.md) [Accessing data in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
