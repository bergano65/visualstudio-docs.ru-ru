---
title: Создание простых данных приложения с помощью WPF и Entity Framework 6
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8909ef785bd721e5b07046329e4841cebc5ec24e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822076"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Создание простых данных приложения с помощью WPF и Entity Framework 6

В этом пошаговом руководстве показано, как создать приложение основные «формы поверх данных» в Visual Studio. Приложение использует SQL Server LocalDB, базы данных "Борей", Entity Framework 6 и Windows Presentation Foundation. Показано, как выполнять основные привязку данных с основного / подробного представления, и она также содержит пользовательские привязки навигатор с кнопками для **Переместить вперед**, **Move Previous**, **переместить в начало**, **Переместить в конец**, **обновление** и **удалить**.

В этой статье рассматривается использование средства данных в Visual Studio и не будет пытаться объяснить базовых технологий в любой глубины. Предполагается, что у вас есть базовые знания о XAML, Entity Framework и SQL. В этом примере также показано архитектуры Model-View-ViewModel (MVVM), которые являются стандартными для приложений WPF. Тем не менее можно скопировать этот код в приложение MVVM с небольшими изменениями.

## <a name="install-and-connect-to-northwind"></a>Установка и подключение к "Борей"

В этом примере используется SQL Server Express LocalDB и базе данных Northwind. Если поставщик данных ADO.NET на этот продукт поддерживает Entity Framework, он должен работать с другими продуктами баз данных SQL так же хорошо.

1.  Если у вас нет SQL Server Express LocalDB, установите его из [странице загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), либо с помощью **установщик Visual Studio**. В **установщик Visual Studio**, можно установить SQL Server Express LocalDB как часть **разработка классических приложений .NET** рабочей нагрузки или в качестве отдельного компонента.

2.  Установка образца базы данных "Борей", выполнив следующие действия:

    1. В Visual Studio откройте **обозреватель объектов SQL Server** окна. (**Обозреватель объектов SQL Server** устанавливается как часть **хранение и обработка данных** рабочей нагрузки в **установщик Visual Studio**.) Разверните **SQL Server** узла. Щелкните правой кнопкой мыши на локальном экземпляре LocalDB и выберите **новый запрос**.

       Откроется окно редактора запросов.

    2. Копировать [скрипт Northwind Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот сценарий T-SQL создает базу данных "Борей" с нуля и заполняет ее данными.

    3. Вставьте сценарий T-SQL в редакторе запросов, а затем выберите **Execute** кнопки.

       Через некоторое время выполнения запроса отобразятся и создания базы данных Northwind.

3.  [Добавление новых подключений](../data-tools/add-new-connections.md) для Northwind.

## <a name="configure-the-project"></a>Настройка проекта

1.  В Visual Studio, выберите **файл** > **New** > **проекта** и создайте новое приложение WPF C#.

2.  Добавьте пакет NuGet Entity Framework 6. В **обозревателе решений**, выберите узел проекта. В главном меню выберите **проекта** > **управление пакетами NuGet**.

     ![Управление пакетами NuGet пункта меню](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3.  В **диспетчер пакетов NuGet**, щелкните **Обзор** ссылку. Entity Framework, вероятно, является верхний пакет в списке. Нажмите кнопку **установить** в правой области и следуйте инструкциям на экране. В окне вывода рассказывается о том, когда установка будет завершена.

     ![Пакет NuGet Entity Framework](../data-tools/media/raddata_vs2015_nuget_ef.png)

4.  Теперь можно использовать Visual Studio для создания модели на основе базы данных "Борей".

## <a name="create-the-model"></a>Создание модели

1. Щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и выберите **добавить** > **новый элемент**. В левой области, в узле C# выберите **данных** и в средней области выберите **ADO.NET Entity Data Model**.

   ![Новый элемент проекта Entity Framework модель](../data-tools/media/raddata-ef-new-project-item.png)

2. Вызов ее `Northwind_model` и выберите **ОК**. **Мастер моделей EDM** открывает. Выберите **конструктор EF из базы данных** и нажмите кнопку **Далее**.

   ![Модель EF из базы данных](../data-tools/media/raddata-ef-model-from-database.png)

3. На следующем экране выберите ваш LocalDB Northwind, соединения и нажмите **Далее**.

4. На следующей странице мастера выберите, какие таблицы, хранимые процедуры и другие объекты базы данных для включения в модель Entity Framework. Разверните узел dbo в представлении в виде дерева и выберите **клиентов**, **заказы**, и **Order Details**. Оставьте параметры по умолчанию и нажмите кнопку **Готово**.

    ![Выбор объектов базы данных для модели](../data-tools/media/raddata-choose-ef-objects.png)

5. Мастер формирует классы C#, которые представляют модель Entity Framework. Классы простых старых классов C# и какие мы databind для пользовательского интерфейса WPF. *.Edmx* файл описывает связи и другие метаданные, который связывает классы с объектами в базе данных. *.Tt* файлы являются шаблоны T4, которые создают код, который работает на модели и сохраните изменения в базе данных. Вы увидите все эти файлы в **обозревателе решений** узле Northwind_model:

      ![Файлы модели EF в обозревателе решений](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    Поверхность конструктора *.edmx* файл можно изменить некоторые свойства и отношения в модели. Мы не будем использовать конструктор в этом пошаговом руководстве.

6. *.Tt* файлы являются универсальными, и вам необходимо настроить один из них для работы с привязка данных WPF, который требует ObservableCollections. В **обозревателе решений**, пока не найдете узел Northwind_model *Northwind_model.tt*. (Убедитесь, что не находится в *. Context.tt* файл, который находится прямо под *.edmx* файл.)

   -   Заменить два вхождения <xref:System.Collections.ICollection> с <xref:System.Collections.ObjectModel.ObservableCollection%601>.

   -   Замените первое вхождение <xref:System.Collections.Generic.HashSet%601> с <xref:System.Collections.ObjectModel.ObservableCollection%601> около строки 51. Не заменяйте второе вхождение HashSet.

   -   Замените только вхождение <xref:System.Collections.Generic> (около строки 431) с <xref:System.Collections.ObjectModel>.

7. Нажмите клавишу **Ctrl**+**Shift**+**B** для сборки проекта. После завершения построения, классы моделей являются видимыми для мастера источников данных.

Теперь все готово для подключения этой модели на страницу XAML, можно просматривать, перемещения и изменения данных.

## <a name="databind-the-model-to-the-xaml-page"></a>DataBind модели на страницу XAML

Можно написать собственный код привязки данных, но гораздо проще позволить Visual Studio сделаем это за вас.

1.  В главном меню выберите **проекта** > **добавить новый источник данных** откроется **мастер настройки источника данных**. Выберите **объект** поскольку вы привязываете для классов модели, а не к базе данных:

     ![Мастер настройки источника данных с источника объекта](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2.  Выберите **клиента**. (Источников для заказов, создаются автоматически из свойства навигации заказов клиента.)

     ![Добавьте классы сущностей в качестве источников данных](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3.  Нажмите кнопку **Готово**.

4.  Перейдите к *MainWindow.xaml* в представлении кода. Мы сохранили известную XAML простой для целей этого примера. Изменение заголовка MainWindow на более описательное и увеличьте его высоту и ширину для 600 x 800 сейчас. Ее можно всегда изменить позже. Теперь добавьте следующие определения три строки в основной сетке, одну строку для кнопок навигации, для сведения о клиентах и один для сетку, которая отображает заказы:

    ```xaml
    <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5.  Теперь откройте *MainWindow.xaml* так, чтобы просмотреть его в конструкторе. В результате **источников данных** окна отображаются как параметр в поле окна Visual Studio рядом с полем **элементов**. Перейдите на вкладку, чтобы открыть окно, или в противном случае щелкните **Shift**+**Alt**+**D** или выберите **представление**  >  **Другие Windows** > **источников данных**. Мы собираемся отображения каждого свойства в классе клиентов в собственном окне отдельного фрагмента текста. Во-первых, щелкните стрелку в **клиентов** поле со списком можно выбрать **сведения**. Затем перетащите узел в средней части области конструктора, чтобы конструктор знает, что необходимо перейти в среднюю строку. Если вы потеряли его, можно указать строку вручную в XAML. По умолчанию элементы управления размещаются по вертикали в элемента сетки, но на этом этапе можно упорядочивать их как вам нравится в форме. Например, может быть целесообразно поместить **имя** текстовое поле в верхней части страницы выше адрес. Пример приложения для этой статьи изменяет порядок полей и размещает их на два столбца.

     ![Привязку к источнику данных клиентов на отдельные элементы управления](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     В представлении кода вы увидите новый `Grid` элементу в строке 1 (посередине) родительского элемента сетки. Сетка содержит родительский `DataContext` атрибут, который относится к CollectionViewSource, который добавляется к `Windows.Resources` элемент. Учитывая этот контекст данных, когда первое текстовое поле выполняет привязку к **адрес**, сопоставляется с таким именем `Address` свойств в текущем `Customer` объекта в CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6.  Если клиент отображается в верхней части окна, требуется для просмотра заказов в нижней половине. Показать заказы в элементе управления представления одной ячейке сетки. Для привязки данных основной / подробности работала должным образом важно привязать к свойству Orders в классе клиентов не на отдельном узле заказов. Перетащите свойство Orders класса клиентов в нижней области формы, таким образом, чтобы, конструктор поместит его в строке 2:

     ![Перетащить классы заказов в виде сетки](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7.  Visual Studio создала весь код привязки, который подключается к событиям модели элементов управления пользовательского интерфейса. Все, что вам нужно выполнить, чтобы просмотреть некоторые данные, является написание кода для заполнения модели. Во-первых, перейдите к *MainWindow.xaml.cs* и добавьте данные-член к классу MainWindow для контекста данных. Этот объект, который был создан для вас, действует примерно элемент управления, который отслеживает изменения и другие события в модели. Вы также добавите логику инициализации конструктора. Начало класса должно выглядеть следующим образом:

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Добавление `using` директив для System.Data.Entity для вызова метода расширения Load в область действия:

     ```csharp
     using System.Data.Entity;
     ```

     Теперь прокрутите вниз и найдите `Window_Loaded` обработчик событий. Обратите внимание на то, что Visual Studio добавляет объект CollectionViewSource. Представляет объект NorthwindEntities, выбранного при создании модели. Давайте добавим код, чтобы `Window_Loaded` таким образом, чтобы весь метод теперь выглядит следующим образом:

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8.  Нажмите клавишу **F5**. Вы увидите сведения для первого клиента, который был извлечен в CollectionViewSource. Вы также увидите их заказов в сетке данных. Форматирование не слишком подробная, так что давайте исправим ее. Можно также создать способ просмотреть другие записи и выполнять основные операции CRUD.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Изменить макет страницы и добавление сеток для новых клиентов и заказы

Расположение по умолчанию, созданные Visual Studio не идеально подходит для вашего приложения, поэтому вручную вносятся некоторые изменения в XAML. Необходимо также некоторые «формы» (которые фактически сетки) позволяют пользователю для добавления нового клиента или заказа. Чтобы иметь возможность добавлять новый customer и order, требуется отдельный набор текстовых полей, которые не привязаны к `CollectionViewSource`. Вы будете управлять какие сетки, пользователь видит в любой момент времени, задав свойство Visible в методы обработчика. Наконец добавить кнопку «Удалить» для каждой строки в таблице заказов, чтобы пользователь мог удалить отдельного заказа.

Во-первых, добавьте следующие стили для `Windows.Resources` элемент в *MainWindow.xaml*:

```xaml
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Left"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="23"/>
</Style>
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Right"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="26"/>
    <Setter Property="Width" Value="120"/>
</Style>
```

Затем замените внешний сетки в целом с этой разметкой:

```xaml
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="New Order Form" FontWeight="Bold"/>
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">
         <DataGrid.Columns>
             <DataGridTemplateColumn>
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>
         </DataGrid.Columns>
     </DataGrid>
 </Grid>
```

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Добавление кнопок для перехода, добавление, обновление и удаление

В приложениях Windows Forms вы получите объект BindingNavigator с кнопками для просмотра строк в базе данных и выполнение основных операций CRUD. WPF предоставляет BindingNavigator, но это достаточно просто для того создать его. Сделать это с помощью кнопок в StackPanel по горизонтали и связать кнопок с командами, которые привязаны к методам в коде программной части.

Состоит из частей четверки логику команды: (1) команды, (2 привязки, (3) кнопок и (4) обработчиками команд в код программной части.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Добавление команд, привязок и кнопки в XAML

1.  Во-первых, добавьте команды в *MainWindow.xaml* внутри `Windows.Resources` элемент:

    ```xaml
    <RoutedUICommand x:Key="FirstCommand" Text="First"/>
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>
    ```

2.  Сопоставляет CommandBinding `RoutedUICommand` событий к методу в коде программной части. Добавьте этот `CommandBindings` после элемента `Windows.Resources` закрывающий тег:

    ```xaml
    <Window.CommandBindings>
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>
    </Window.CommandBindings>
    ```

3.  Теперь добавьте `StackPanel` навигации, добавить, удалить и обновления с помощью кнопок. Во-первых, добавьте этот стиль к `Windows.Resources`:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Во-вторых, вставьте этот код сразу после `RowDefinitions` для внешнего `Grid` элемент, расположенной в верхней части страницы XAML:

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>Добавьте в класс MainWindow обработчиков команд

Код программной части сводится к минимуму, за исключением методы добавления и удаления. Навигации выполняется путем вызова методов на свойство представления CollectionViewSource. `DeleteOrderCommandHandler` Показано, как провести каскадное удаление заказа. Нам нужно сначала удалить данные заказа, связанные с ним. `UpdateCommandHandler` Добавляет к коллекции нового клиента или заказа, в противном случае просто вносит изменения, внесенные пользователем в текстовых полях существующего клиента или заказа.

Добавьте эти методы обработчика к классу MainWindow в *MainWindow.xaml.cs*. Если ваш CollectionViewSource для таблицы Customers имеет другое имя, необходимо изменить имя в каждом из этих методов:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Запуск приложения

Чтобы начать отладку, нажмите клавишу **F5**. Вы увидите данные в сетке и кнопки навигации должен работать соответствующим образом. Щелкните **зафиксировать** для добавления нового клиента или заказа в модель, после ввода данных. Щелкните **отменить** восстановить нового клиента или новую форму заказа без сохранения данных. Можно вносить изменения в существующие клиенты и заказы непосредственно в текстовые поля, и эти изменения автоматически записываются в модели.

## <a name="see-also"></a>См. также

- [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Документация по Entity Framework](/ef/)