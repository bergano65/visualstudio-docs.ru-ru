---
title: Bind WPF controls to a WCF data service | Microsoft Docs
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
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a3d1aab68e3dc9f33e0b3e9f9a5665d59f6f2ddc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299407"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Привязка элементов управления WPF к службе данных WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве вы создадите приложение WPF, содержащее элементы управления с привязкой к данным. Эти элементы управления привязаны к записям клиентов, инкапсулированным в [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]. Вы также добавите кнопки, позволяющие клиентам просматривать и обновлять записи.

 В данном пошаговом руководстве рассмотрены следующие задачи:

- Создание модели данных с использованием сущностей (EDM), сформированной из данных в учебной базе данных AdventureWorksLT.

- Creating a [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] that exposes the data in the Entity Data Model to a WPF application.

- Создание набора элементов управления с привязкой к данным путем перетаскивания элементов из окна **Источники данных** в конструктор WPF.

- Создание кнопок для перехода вперед и назад по записям клиентов.

- Creating a button that saves changes to data in the controls to the [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] and the underlying data source.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Необходимые компоненты
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- Доступ к запущенному экземпляру SQL Server или SQL Server Express с подключенной учебной базой данных AdventureWorksLT. You can download the AdventureWorksLT database from the [CodePlex Web site](https://go.microsoft.com/fwlink/?linkid=87843).

  Перед изучением приведенных ниже концепций будет полезно, хотя и не обязательно, ознакомиться со следующим пошаговым руководством.

- Службы данных WCF. For more information, see [Overview](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).

- Модели данных в [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)].

- Модели EDM и ADO.NET Entity Framework. For more information, see [Entity Framework Overview](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).

- Работа с Конструктором WPF. For more information, see [WPF and Silverlight Designer Overview](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- Привязка данных WPF. Более подробную информацию см. в разделе [Общие сведения о связывании данных](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="create-the-service-project"></a>Create the service project
 Начните работу с данным пошаговым руководством с создания проекта для [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

#### <a name="to-create-the-service-project"></a>Порядок создания проекта службы

1. Запустите Visual Studio.

2. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

3. Разверните **Visual C#** или **Visual Basic** и выберите **Веб-сайт**.

4. Выберите шаблон проекта **Веб-приложение ASP.NET**.

5. In the **Name** box, type `AdventureWorksService` and click **OK**.

     Visual Studio creates the `AdventureWorksService` project.

6. В **обозревателе решений** щелкните правой кнопкой мыши **Default.aspx** и выберите пункт **Удалить**. Этот файл для прохождения данного руководства не требуется.

## <a name="create-an-entity-data-model-for-the-service"></a>Create an Entity Data Model for the service
 Чтобы предоставить данные приложению с помощью [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], следует определить модель данных для этой службы. The [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] supports two types of data models: Entity Data Models, and custom data models that are defined by using common language runtime (CLR) objects that implement the <xref:System.Linq.IQueryable%601> interface. В данном пошаговом руководстве вы создадите модель EDM для использования в качестве модели данных.

#### <a name="to-create-an-entity-data-model"></a>Создание модели EDM

1. В меню **Проект** выберите пункт **Добавить новый элемент**.

2. В списке "Установленные шаблоны" щелкните **Данные** и выберите элемент проекта **Модель ADO.NET EDM**.

3. Change the name to `AdventureWorksModel.edmx`, and click **Add**.

     Открывается **Мастер моделей EDM**.

4. На странице **Выбор содержимого модели** щелкните **Создать из базы данных** и нажмите кнопку **Далее**.

5. На странице **Выбор подключения к базе данных** выберите один из следующих параметров:

    - Если подключение к учебной базе данных AdventureWorksLT доступно в раскрывающемся списке, то выберите его.

    - Щелкните **Создать подключение** и создайте подключение к базе данных AdventureWorksLT.

6. На странице **Выбор подключения базы данных** убедитесь, что выбран параметр **Сохранить параметры соединения сущности в App.Config как**, а затем нажмите кнопку **Далее**.

7. На странице **Выбор объектов базы данных** разверните узел **Таблицы** и выберите таблицу **SalesOrderHeader**.

8. Нажмите кнопку **Готово**.

## <a name="create-the-service"></a>Создание службы
 Create a [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] to expose the data in the Entity Data Model to a WPF application.

#### <a name="to-create-the-service"></a>Создание службы

1. В меню **Проект** выберите пункт **Добавить новый элемент**.

2. In the Installed Templates list, click **Web**, and then select the **WCF Data Service** project item.

3. In the **Name** box, type `AdventureWorksService.svc`, and click **Add**.

     Visual Studio adds the `AdventureWorksService.svc` to the project.

## <a name="configure-the-service"></a>Настройка службы
 Вам необходимо настроить службу на использование созданной модели EDM.

#### <a name="to-configure-the-service"></a>Порядок настройки службы

1. In the `AdventureWorks.svc` code file, replace the `AdventureWorksService` class declaration with the following code.

     [!code-csharp[Data_WPFWCF#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs#1)]
     [!code-vb[Data_WPFWCF#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb#1)]

     This code updates the `AdventureWorksService` class, so that it derives from a <xref:System.Data.Services.DataService%601> that operates on the `AdventureWorksLTEntities` object context class in your Entity Data Model. Он также обновляет метод `InitializeService`, чтобы предоставить клиентам службы полный доступ на чтение/запись к сущности `SalesOrderHeader`.

2. Соберите проект и убедитесь в отсутствии ошибок.

## <a name="create-the-wpf-client-application"></a>Create the WPF client application
 Чтобы отобразить данные из [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], создайте новое приложение WPF с источником данных, основанным на этой службе. Позднее в этом пошаговом руководстве вы добавите в приложение элементы управления с привязкой к данным.

#### <a name="to-create-the-wpf-client-application"></a>Порядок создания клиентского приложения WPF

1. В **обозревателе решений** щелкните правой кнопкой мыши узел решения, выберите команду **Добавить** и пункт **Новый проект**.

2. В диалоговом окне **Новый проект** разверните узел **Visual C#** или **Visual Basic**, а затем выберите **Windows**.

3. Выберите шаблон проекта **Приложение WPF**.

4. В поле **Имя** введите `AdventureWorksSalesEditor`, а затем нажмите кнопку **ОК**.

     Visual Studio adds the `AdventureWorksSalesEditor` project to the solution.

5. В меню **Данные** выберите команду **Показать источники данных**.

     Открывается окно **Источники данных**.

6. В окне **Источники данных** выберите **Добавить новый источник данных**.

     Открывается **мастер настройки источника данных**.

7. На странице **Выбор типа источника данных мастера** выберите **Служба** и нажмите кнопку **Далее**.

8. В диалоговом окне **Добавление ссылки на службу** щелкните элемент **Найти**.

     Visual Studio searches the current solution for available services, and adds `AdventureWorksService.svc` to the list of available services in the **Services** box.

9. In the **Namespace** box, type `AdventureWorksService`.

10. В поле **Службы** щелкните **AdventureWorksService.svc** и нажмите кнопку **ОК**.

     Visual Studio downloads the service information, and then returns to the **Data Source Configuration** wizard.

11. На странице **Добавление ссылки на службу** нажмите кнопку **Готово**.

     Visual Studio добавляет узлы, которые представляют данные, возвращаемые службой в окно **Источники данных**.

## <a name="define-the-user-interface-of-the-window"></a>Define the user interface of the window
 Добавьте несколько кнопок в окно, изменив в XAML в конструкторе WPF. Позднее в рамках данного пошагового руководства вы добавите код, позволяющий пользователям просматривать и обновлять торговые записи с помощью этих кнопок.

#### <a name="to-create-the-window-layout"></a>Создание макета окна

1. In **Solution Explorer**, double-click MainWindow.xaml.

     Открывается окно в Конструкторе WPF.

2. В представлении [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] конструктора добавьте следующий код между тегами `<Grid>`:

    ```
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="525" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3. Выполните построение проекта.

## <a name="create-the-data-bound-controls"></a>Create the data-bound controls
 Create controls that display customer records by dragging the `SalesOrderHeaders` node from the **Data Sources** window to the designer.

#### <a name="to-create-the-data-bound-controls"></a>Порядок создания элементов управления с привязкой к данным

1. В окне **Источники данных** щелкните раскрывающееся меню для узла **SalesOrderHeaders** и выберите команду **Сведения**.

2. Разверните узел **SalesOrderHeaders**.

3. Для этого примера некоторые поля не отображаются, поэтому щелкните раскрывающееся меню рядом со следующими узлами и выберите **Нет**:

   - **CreditCardApprovalCode**

   - **ModifiedDate**

   - **OnlineOrderFlag**

   - **RevisionNumber**

   - **rowguid**

     Это действие не позволяет Visual Studio создать элементы управления с привязкой к данным для этих узлов на следующем шаге. For this walkthrough, assume that the end user does not need to see this data.

4. Из окна **Источники данных** перетащите узел **SalesOrderHeaders** на строку сетки под строкой с кнопками.

    Visual Studio формирует XAML и код, который создает набор элементов управления, привязанных к данным в таблице **Продукт**. For more information about the generated XAML and code, see [Bind WPF controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

5. Щелкните в конструкторе текстовое поле рядом с меткой **Идентификатор клиента**.

6. В окне **Свойства** установите флажок рядом со свойством **IsReadOnly**.

7. Установите свойство **IsReadOnly** для каждого из следующих текстовых полей:

   - **Номер заказа на поставку**

   - **Код заказа на продажу**

   - **Номер заказа на продажу**

## <a name="load-the-data-from-the-service"></a>Загрузка данных из службы
 Use the service proxy object to load sales data from the service. Then assign the returned data to the data source for the <xref:System.Windows.Data.CollectionViewSource> in the WPF window.

#### <a name="to-load-the-data-from-the-service"></a>Порядок загрузки данных из службы

1. В конструкторе, чтобы создать `Window_Loaded` обработчик событий, дважды щелкните текст, который считывает: **MainWindow**.

2. Замените этот обработчик событий следующим кодом. Замените адрес *localhost* в этом коде на локальный адрес вашего компьютера разработчика.

     [!code-csharp[Data_WPFWCF#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFWCF#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#2)]

## <a name="navigatesales-records"></a>Navigatesales records
 Добавьте код, позволяющий пользователям выполнять прокрутку торговых записей с помощью кнопок **\<** и **>** .

#### <a name="to-enable-users-to-navigate-sales-records"></a>Предоставление пользователям возможности навигации по торговым записям

1. В конструкторе дважды щелкните кнопку **<** на поверхности окна.

     Visual Studio открывает файл кода программной части и создает обработчик событий `backButton_Click` для события <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Добавьте следующий код в созданный обработчик событий `backButton_Click`:

     [!code-csharp[Data_WPFWCF#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFWCF#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#3)]

3. Вернитесь в конструктор и дважды щелкните кнопку **>** .

     Visual Studio открывает файл кода программной части и создает обработчик событий `nextButton_Click` для события <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

4. Добавьте следующий код в созданный обработчик событий `nextButton_Click`:

     [!code-csharp[Data_WPFWCF#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFWCF#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#4)]

## <a name="saving-changes-to-sales-records"></a>Saving changes to sales records
 Add code that enables users to both view and save changes to sales records by using the **Save changes** button.

#### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Добавление возможности сохранения изменений в торговых записях

1. В конструкторе дважды щелкните кнопку **Сохранить изменения**.

     Visual Studio открывает файл кода программной части и создает обработчик событий `saveButton_Click` для события <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Добавьте следующий код в обработчик событий `saveButton_Click`.

     [!code-csharp[Data_WPFWCF#5](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#5)]
     [!code-vb[Data_WPFWCF#5](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#5)]

## <a name="testing-the-application"></a>Тестирование приложения
 Выполните сборку и запуск приложения, чтобы убедиться, что вы можете просмотреть и обновить записи клиентов.

#### <a name="to-test-the-application"></a>Тестирование приложения

1. On **Build** menu, click **Build Solution**. Убедитесь, что сборка решения выполняется без ошибок.

2. Press **Ctrl+F5**.

     Visual Studio запускает проект **AdventureWorksService** без его отладки.

3. В **обозревателе решений** щелкните правой кнопкой мыши проект **AdventureWorksSalesEditor**.

4. В области **Отладка** контекстного меню выберите команду **Запустить новый экземпляр**.

     Выполняется запуск приложения. Проверьте следующее.

    - Текстовые поля отображают разные поля данных из первой торговой записи, имеющей код заказа на продажу **71774**.

    - Вы можете нажать кнопку **>** или **<** для перехода по другим торговым записям.

5. Введите текст в поле **Комментарий** для одной из торговых записей, а затем нажмите кнопку **Сохранить изменения**.

6. Закройте приложение и снова запустите его из Visual Studio.

7. Перейдите к измененной торговой записи и убедитесь, что изменения сохранились после перезапуска приложения.

8. Закройте приложение.

## <a name="next-steps"></a>Следующие шаги
 После прохождения пошагового руководства вы можете выполнить следующие задачи.

- Узнайте, как использовать окно **Источники данных** в Visual Studio для привязки элементов управления WPF к другим типам источников данных. For more information, see [Bind WPF controls to a dataset](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Узнайте, как использовать окно **Источники данных** в Visual Studio для отображения связанных данных (то есть данных в отношении "родитель — потомок") в элементах управления WPF. For more information, see [Walkthrough: Displaying Related Data in a WPF Application](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).

## <a name="see-also"></a>См. также раздел
 [Bind WPF controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Bind WPF controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [Bind WPF controls to a dataset](../data-tools/bind-wpf-controls-to-a-dataset.md) [Overview](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb) [Entity Framework Overview](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0) [WPF and Silverlight Designer Overview](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62) [Data Binding Overview](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)
