---
title: Привязка элементов управления WPF к службе данных WCF
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8152a02df8f335a92024134dde89b45d2f3e115a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31927364"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Привязка элементов управления WPF к службе данных WCF

В этом пошаговом руководстве вы создадите приложение WPF, содержащее элементы управления с привязкой к данным. Эти элементы управления привязаны к записям клиентов, инкапсулированным в [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]. Вы также добавите кнопки, позволяющие клиентам просматривать и обновлять записи.

В данном пошаговом руководстве рассмотрены следующие задачи:

- Создание модели данных с использованием сущностей (EDM), сформированной из данных в учебной базе данных AdventureWorksLT.

- Создание [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] , предоставляющего данные в модели EDM приложению WPF.

- Создание набора элементов управления с привязкой к данным путем перетаскивания элементов из **источники данных** в конструктор WPF.

- Создание кнопок для перехода вперед и назад по записям клиентов.

- Создание кнопки, сохраняющий изменения данных в элементах управления для [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] и базовом источнике данных.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Предварительные требования
Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

-   Доступ к запущенному экземпляру SQL Server или SQL Server Express с подключенной учебной базой данных AdventureWorksLT. Можно загрузить базу данных AdventureWorksLT с [веб-сайта CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).

Перед изучением приведенных ниже концепций будет полезно, хотя и не обязательно, ознакомиться со следующим пошаговым руководством.

-   Службы данных WCF. Дополнительные сведения см. в разделе [Обзор](/dotnet/framework/data/wcf/wcf-data-services-overview).

-   Модели данных в [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].

-   Модели EDM и ADO.NET Entity Framework. Дополнительные сведения см. в разделе [Общие сведения об Entity Framework](/dotnet/framework/data/adonet/ef/overview).

-   Привязка данных WPF. Более подробную информацию см. в разделе [Общие сведения о связывании данных](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Создание проекта службы
Начните работу с данным пошаговым руководством с создания проекта для [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

### <a name="to-create-the-service-project"></a>Порядок создания проекта службы

1.  Запустите Visual Studio.

2.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

3.  Разверните **Visual C#** или **Visual Basic**, а затем выберите **Web**.

4.  Выберите шаблон проекта **Веб-приложение ASP.NET**.

5.  В **имя** введите `AdventureWorksService` и нажмите кнопку **ОК**.

     Visual Studio создает `AdventureWorksService` проекта.

6.  В **обозревателе решений**, щелкните правой кнопкой мыши **Default.aspx** и выберите **удалить**. Этот файл для прохождения данного руководства не требуется.

## <a name="create-an-entity-data-model-for-the-service"></a>Создание модели EDM для службы
Чтобы предоставить данные приложению с помощью [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], следует определить модель данных для этой службы. [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] Поддерживает модели данных двух типов: модели EDM и настраиваемые модели данных, определенных с помощью объектов среды выполнения (CLR), реализующие <xref:System.Linq.IQueryable%601> интерфейса. В данном пошаговом руководстве вы создадите модель EDM для использования в качестве модели данных.

### <a name="to-create-an-entity-data-model"></a>Создание модели EDM

1.  В меню **Проект** выберите пункт **Добавить новый элемент**.

2.  В списке "Установленные шаблоны", нажмите кнопку **данные**, а затем выберите **ADO.NET Entity Data Model** элемент проекта.

3.  Измените имя на `AdventureWorksModel.edmx`и нажмите кнопку **добавить**.

     **Модели EDM** откроется мастер.

4.  На **Выбор содержимого модели** щелкните **создать из базы данных**и нажмите кнопку **Далее**.

5.  На **Выбор подключения к данным** выберите один из следующих вариантов:

    -   Если подключение к учебной базе данных AdventureWorksLT доступно в раскрывающемся списке, то выберите его.

    -   Нажмите кнопку **новое подключение**и создайте подключение к базе данных AdventureWorksLT.

6.  На **Выбор подключения к данным** убедитесь, что **сохранить настройки подключения сущности в App.Config как** параметр выбран и нажмите кнопку **Далее**.

7.  На **Выбор объектов базы данных** разверните **таблиц**, а затем выберите **SalesOrderHeader** таблицы.

8.  Нажмите кнопку **Готово**.

## <a name="create-the-service"></a>Создание службы
Создать [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] для предоставления данных в модели EDM приложению WPF.

### <a name="to-create-the-service"></a>Создание службы

1.  На **проекта** последовательно выберите пункты **Добавление нового элемента**.

2.  В списке "Установленные шаблоны", нажмите кнопку **Web**, а затем выберите **службы данных WCF** элемент проекта.

3.  В **имя** введите `AdventureWorksService.svc`и нажмите кнопку **добавить**.

     Visual Studio добавляет `AdventureWorksService.svc` в проект.

## <a name="configure-the-service"></a>Настройка службы
Вам необходимо настроить службу на использование созданной модели EDM.

### <a name="to-configure-the-service"></a>Порядок настройки службы

1.  В `AdventureWorks.svc` файл кода, замените `AdventureWorksService` класса следующим кодом.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     Этот код обновляет `AdventureWorksService` класса, чтобы он был производным от <xref:System.Data.Services.DataService%601> , работающего с `AdventureWorksLTEntities` объекта класса контекста в вашей модели EDM. Он также обновляет метод `InitializeService`, чтобы предоставить клиентам службы полный доступ на чтение/запись к сущности `SalesOrderHeader`.

2.  Соберите проект и убедитесь в отсутствии ошибок.

## <a name="create-the-wpf-client-application"></a>Создание клиентского приложения WPF
Чтобы отобразить данные из [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], создайте новое приложение WPF с источником данных, основанным на этой службе. Позднее в этом пошаговом руководстве вы добавите в приложение элементы управления с привязкой к данным.

### <a name="to-create-the-wpf-client-application"></a>Порядок создания клиентского приложения WPF

1.  В **обозревателе решений**, щелкните правой кнопкой мыши узел решения, нажмите кнопку **добавить**и выберите **новый проект**.

2.  В **новый проект** диалогового окна разверните **Visual C#** или **Visual Basic**, а затем выберите **Windows**.

3.  Выберите **приложение WPF** шаблона проекта.

4.  В **имя** введите `AdventureWorksSalesEditor`и нажмите кнопку **ОК**.

     Visual Studio добавляет `AdventureWorksSalesEditor` проекта в решение.

5.  В меню **Данные** выберите команду **Показать источники данных**.

     **Источники данных** открывается окно.

6.  В окне **Источники данных** выберите **Добавить новый источник данных**.

     **Конфигурации источника данных** откроется мастер.

7.  В **Выбор типа источника данных** странице мастера выберите **службы**, а затем нажмите кнопку **Далее**.

8.  В **добавить ссылку на службу** диалоговое окно, нажмите кнопку **Discover**.

     Visual Studio выполняет поиск текущего решения для доступных служб, а также добавляет `AdventureWorksService.svc` в список доступных служб в **служб** поле.

9. В **имен** введите `AdventureWorksService`.

10. В **службы** щелкните **AdventureWorksService.svc**, а затем нажмите кнопку **ОК**.

     Visual Studio загружает сведения о службе и затем возвращает **конфигурации источника данных** мастера.

11. В **добавить ссылку на службу** щелкните **Готово**.

     Visual Studio добавляет узлы, представляющие данные, возвращаемые службой для **источники данных** окна.

## <a name="define-the-user-interface-of-the-window"></a>Определение пользовательского интерфейса окна
Добавьте несколько кнопок в окно, изменив в XAML в конструкторе WPF. Позднее в рамках данного пошагового руководства вы добавите код, позволяющий пользователям просматривать и обновлять торговые записи с помощью этих кнопок.

### <a name="to-create-the-window-layout"></a>Создание макета окна

1.  В **обозревателе решений**, дважды щелкните **MainWindow.xaml**.

     Открывается окно в Конструкторе WPF.

2.  В представлении [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] конструктора добавьте следующий код между тегами `<Grid>`:

    ```xaml
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="525" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3.  Выполните построение проекта.

## <a name="create-the-data-bound-controls"></a>Создавать элементы управления с привязкой к данным
Создайте элементы управления, отображающие записи клиентов, перетащив `SalesOrderHeaders` узел из **источники данных** в конструктор.

### <a name="to-create-the-data-bound-controls"></a>Порядок создания элементов управления с привязкой к данным

1.  В **источники данных** окно, щелкните раскрывающееся меню для **SalesOrderHeaders** , а затем установите **сведения**.

2.  Разверните **SalesOrderHeaders** узла.

3.  Для этого примера некоторые поля не будут отображаться, поэтому щелкните раскрывающееся меню рядом со следующими узлами и выберите **нет**:

    -   **CreditCardApprovalCode**

    -   **ModifiedDate**

    -   **OnlineOrderFlag**

    -   **RevisionNumber**

    -   **ROWGUID**

    Это действие не позволяет Visual Studio создать элементы управления с привязкой к данным для этих узлов на следующем шаге. В данном пошаговом руководстве предположим, что конечному пользователю не требуется просматривать эти данные.

4.  Из **источники данных** перетащите **SalesOrderHeaders** узел на строку сетки под строкой, содержащей кнопки.

     Visual Studio формирует XAML и код, который создает набор элементов управления, привязанных к данным в **продукта** таблицы. Дополнительные сведения о созданный язык XAML и код см. в разделе [WPF привязать элементы управления к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5.  В конструкторе щелкните текстовое поле рядом с **Customer ID** метки.

6.  В **свойства** окна, установите флажок рядом с полем **IsReadOnly** свойство.

7.  Задать **IsReadOnly** свойство для каждого из следующих текстовых полей:

    -   **Номер заказа на покупку**

    -   **Идентификатор заказа на продажу**

    -   **Номер заказа на продажу**

## <a name="load-the-data-from-the-service"></a>Загрузка данных из службы
Используйте прокси-объект службы для загрузки данных о продажах из службы. Затем назначьте возвращенные данные источнику данных для <xref:System.Windows.Data.CollectionViewSource> в окне WPF.

### <a name="to-load-the-data-from-the-service"></a>Порядок загрузки данных из службы

1.  В конструкторе, чтобы создать `Window_Loaded` обработчика событий, дважды щелкните текст, который считывает: **MainWindow**.

2.  Замените этот обработчик событий следующим кодом. Убедитесь, что Вы заменили *localhost* адрес в этом коде на локальный адрес вашего компьютера разработчика.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>Навигации по торговым записям
Добавьте код, позволяющий пользователям выполнять прокрутку торговых записей с помощью **\<** и **>** кнопки.

### <a name="to-enable-users-to-navigate-sales-records"></a>Предоставление пользователям возможности навигации по торговым записям

1.  В конструкторе, дважды щелкните **<** кнопки на поверхности окна.

     Visual Studio открывает файл кода программной части и создает новую `backButton_Click` обработчик событий для <xref:System.Windows.Controls.Primitives.ButtonBase.Click> события.

2.  Добавьте следующий код в созданный обработчик событий `backButton_Click`:

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3.  Вернитесь в конструктор и дважды щелкните **>** кнопки.

     Visual Studio открывает файл кода программной части и создает новую `nextButton_Click` обработчик событий для <xref:System.Windows.Controls.Primitives.ButtonBase.Click> события.

4.  Добавьте следующий код в созданный обработчик событий `nextButton_Click`:

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="saving-changes-to-sales-records"></a>Сохранение изменений в торговых записях
Добавьте код, который позволяет пользователям просматривать и сохранять изменения в торговых записях с помощью **сохранить изменения** кнопки.

### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Добавление возможности сохранения изменений в торговых записях

1.  В конструкторе, дважды щелкните **сохранить изменения** кнопки.

     Visual Studio открывает файл кода программной части и создает новую `saveButton_Click` обработчик событий для <xref:System.Windows.Controls.Primitives.ButtonBase.Click> события.

2.  Добавьте следующий код в обработчик событий `saveButton_Click`.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="testing-the-application"></a>Тестирование приложения
Выполните сборку и запуск приложения, чтобы убедиться, что вы можете просмотреть и обновить записи клиентов.

### <a name="to-test-the-application"></a>Тестирование приложения

1.  На **построения** меню, нажмите кнопку **построить решение**. Убедитесь, что сборка решения выполняется без ошибок.

2.  Нажмите клавишу **сочетание клавиш Ctrl + F5**.

     Visual Studio запускает **AdventureWorksService** проекта без его отладки.

3.  В **обозревателе решений**, щелкните правой кнопкой мыши **AdventureWorksSalesEditor** проекта.

4.  В контекстном меню в разделе **отладки**, нажмите кнопку **запустить новый экземпляр**.

     Выполняется запуск приложения. Проверьте следующее.

    -   Текстовые поля отображают разные поля данных из первой торговой записи, имеющей код заказа на продажу **71774**.

    -   Можно щелкнуть **>** или **<** для перехода по другим торговым записям.

5.  В одной из записей о продажах, введите текст в **комментарий** , а затем щелкните **сохранить изменения**.

6.  Закройте приложение и снова запустите его из Visual Studio.

7.  Перейдите к измененной торговой записи и убедитесь, что изменения сохранились после перезапуска приложения.

8.  Закройте приложение.

## <a name="next-steps"></a>Следующие шаги

После прохождения пошагового руководства вы можете выполнить следующие задачи.

-   Сведения об использовании **источники данных** окно в Visual Studio для привязки WPF элементы управления к другим типам источников данных. Дополнительные сведения см. в разделе [WPF привязать элементы управления к набору данных](../data-tools/bind-wpf-controls-to-a-dataset.md).

-   Сведения об использовании **источники данных** окна в Visual Studio для отображения связанных данных (то есть данные в иерархическом отношении) в элементах управления WPF. Дополнительные сведения см. в разделе [Пошаговое руководство: отображение связанных данных в приложении WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>См. также

- [Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Привязка элементов управления WPF к набору данных](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [Общие сведения о WCF (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Общие сведения об Entity Framework (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Обзор (.NET Framework) привязка данных](/dotnet/framework/wpf/data/data-binding-overview)