---
title: Создание простого приложения для данных с WPF и Entity Framework 6 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 403415eaf8a882efdd63fdb9a73b5489b91f2529
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651085"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Создание простого приложения для обработки данных с помощью WPF и Entity Framework 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом валксаугх показано, как создать базовое приложение "формы для данных" в Visual Studio с помощью SQL Server LocalDB, базы данных Northwind, Entity Framework 6 и Windows Presentation Foundation. В нем показано, как выполнить базовую привязку данных к представлению «основной/подробности», а также имеется пользовательский «навигатор привязки» с кнопками «переместить далее», «переместить назад», «перейти к началу», «переместить в конец», «обновить» и «удалить».

 Эта статья посвящена использованию средств для данных в Visual Studio и не пытается объяснить основные технологии в любой глубине. Предполагается, что у вас есть базовые знания XAML, Entity Framework и SQL. В этом примере также не демонстрируется архитектура MVVM, которая является стандартом для приложений WPF. Однако вы можете скопировать этот код в собственное приложение MVVM, используя очень мало изменений.

## <a name="install-and-connect-to-northwind"></a>Установка и подключение к Northwind
 В этом примере используется SQL Server Express LocalDB и образец базы данных Northwind. Он должен работать с другими продуктами базы данных SQL, а также в том случае, если поставщик данных ADO.NET для этого продукта поддерживает Entity Framework.

1. Если вы еще не сделали это, установите SQL Server 2014 LocalDB Express 32 bit со [страницы загрузки SQL Serverных выпусков](https://www.microsoft.com/sql-server/sql-server-editions-express).

2. Установите учебную базу данных Northwind, следуя приведенным ниже инструкциям. [установите SQL Server образцы баз данных](../data-tools/install-sql-server-sample-databases.md).

3. [Добавление новых подключений](../data-tools/add-new-connections.md) для базы данных Northwind.

## <a name="configure-the-project"></a>Настройка проекта

1. В Visual Studio выберите **файл &#124; новый проект** , а затем создайте новое приложение WPF на C#.

2. Далее мы добавим пакет NuGet для Entity Framework 6. В обозреватель решений выберите узел проекта. В главном меню выберите **проект &#124; Управление пакетами NuGet...**

     ![Пункт меню "Управление пакетами NuGet"](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")

3. В диспетчере пакетов NuGet щелкните ссылку **Обзор** . Entity Framework, вероятно, является верхним пакетом в списке. Щелкните **установить** на правой панели и следуйте инструкциям на экране. После завершения установки появится окно вывод.

     ![Entity Framework пакет NuGet](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")

4. Теперь можно использовать Visual Studio для создания модели на основе базы данных Northwind.

## <a name="create-the-model"></a>Создание модели

1. Щелкните правой кнопкой мыши узел проекта в обозреватель решений и выберите **добавить &#124; новый элемент**. В левой области в узле C# выберите **данные** и в средней области выберите **ADO.NET EDM**.

    ![Новый элемент проекта Entity Framework Model](../data-tools/media/raddata-ef-new-project-item.png "Элемент нового проекта раддата EF")

2. Вызовите модель `Northwind_model` и нажмите кнопку ОК. Откроется **мастер EDM**. Выберите элемент **конструктор EF из базы данных** , а затем нажмите кнопку **Далее**.

    ![Модель EF из базы данных](../data-tools/media/raddata-ef-model-from-database.png "Модель EF раддата из базы данных")

3. На следующем экране выберите подключение к LocalDB Northwind и нажмите кнопку **Далее**.

4. На следующей странице мастера мы выбираем, какие таблицы, хранимые процедуры и другие объекты базы данных включить в модель Entity Framework. Разверните узел dbo в представлении в виде дерева и выберите Customers, Orders и Order Details. Оставьте значения по умолчанию и нажмите кнопку **Готово**.

    ![Выбор объектов базы данных для модели](../data-tools/media/raddata-choose-ef-objects.png "раддата выбрать объекты EF")

5. Мастер создает классы C#, представляющие модель Entity Framework. Это простые старые классы C#, которые мы будем привязку к пользовательскому интерфейсу WPF. Файл EDMX описывает связи и другие метаданные, связывающие классы с объектами в базе данных.  TT — это шаблоны T4, которые создают код, который будет обрабатывать модель, и сохраняет изменения в базе данных. Все эти файлы можно просмотреть в обозреватель решений в узле Northwind_model.

    ![Файлы модели обозреватель решений EF](../data-tools/media/raddata-solution-explorer-ef-model-files.png "раддата обозреватель решений файлы модели EF")

    Область конструктора для файла EDMX позволяет изменять некоторые свойства и связи в модели. Мы не будем использовать конструктор в этом пошаговом руководстве.

6. TT-файлы предназначены для общего назначения, и нам нужно настроить один из них для работы с DataBinding WPF, что требует Обсерваблеколлектионс.  В обозреватель решений разверните узел Northwind_model, пока не найдете Northwind_model. tt. (Убедитесь, что вы **не** используете *. Файл Context. TT, который находится непосредственно под EDMX-файлом).

   - Замените два вхождения <xref:System.Collections.ICollection> на <xref:System.Collections.ObjectModel.ObservableCollection%601> .

   - Замените первое вхождение <xref:System.Collections.Generic.HashSet%601> на <xref:System.Collections.ObjectModel.ObservableCollection%601> около строки 51. Не заменять второе вхождение hashing

   - Замените единственное вхождение <xref:System.Collections.Generic> (около строки 334) на <xref:System.Collections.ObjectModel> .

7. Нажмите клавиши **CTRL + SHIFT + B** , чтобы выполнить сборку проекта. По завершении сборки классы модели видимы в мастере источников данных.

   Теперь мы готовы к подключению этой модели к XAML-странице, чтобы можно было просматривать, перемещать и изменять данные.

## <a name="databind-the-model-to-the-xaml-page"></a>Привязка модели к странице XAML
 Можно написать собственный код привязки данных, но гораздо проще позволить Visual Studio сделать это самостоятельно.

1. В главном меню выберите **проект &#124; добавить новый источник данных** , чтобы открыть **Мастер настройки источника данных**. Выберите **объект** , так как привязка выполняется к классам модели, а не к базе данных.

     ![Мастер настройки источника данных с источником объекта](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "Мастер настройки источника данных раддата с источником объекта")

2. Выберите клиента.  (Источники для заказов будут автоматически созданы из свойства навигации Orders в Customer.)

     ![Добавление классов сущностей в качестве источников данных](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "раддата Добавление классов сущностей в качестве источников данных")

3. Нажмите кнопку **Готово**.

4. Перейдите к файлу MainWindow. XAML в представлении кода. Мы собираемся сделать код XAML очень простым для целей этого примера. Измените заголовок MainWindow на что-то более описательное и увеличьте его высоту и ширину до 600 x 800. Вы всегда можете изменить его позже. Теперь добавьте эти три определения строк в главную сетку, одну строку для кнопок навигации, одну для сведений клиента, одну для сетки, которая показывает их заказы:

    ```xaml
    <Grid.RowDefinitions>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="*"/>
           </Grid.RowDefinitions>
    ```

5. Теперь откройте файл MainWindow. XAML, чтобы просмотреть его в конструкторе. Это приведет к тому, что окно Источники данных будет отображаться в виде параметра в поле окна Visual Studio рядом с областью элементов. Щелкните вкладку, чтобы открыть окно, или нажмите **SHIFT + ALT + D** или выберите **View &#124; другие &#124; источники данных Windows**. Мы будем отображать каждое свойство в классе Customers в отдельном текстовом поле. Сначала щелкните стрелку в поле со списком клиенты и выберите **сведения**. Затем перетащите узел в среднюю часть области конструктора, чтобы разработчик знал, что он должен находиться в средней строке.  В случае его невозможности вручную указать строку в XAML. По умолчанию элементы управления размещаются вертикально в элементе Grid, но на этом этапе их можно расположить в форме.  Например, может иметь смысл разместить текстовое поле Name сверху, над адресом. Пример приложения для этой статьи переупорядочивает поля и перемещает их в два столбца.

     ![Привязка источника данных клиентов к отдельным элементам управления](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "Привязка источника данных клиентов раддата к отдельным элементам управления")

     В представлении кода теперь можно увидеть новый `Grid` элемент в строке 1 (средняя строка) родительской сетки. Родительская сетка имеет `DataContext` атрибут, который ссылается на CollectionViewSource, который был добавлен к `Windows.Resources` элементу. Учитывая этот контекст данных, когда первое текстовое поле, например, привязывается к "Address", имя которого сопоставляется с `Address` свойством в текущем `Customer` объекте в CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Когда клиент отображается в верхней половине окна, нужно просмотреть заказы в нижней половине. Заказы будут показаны в одном элементе управления «сетка». Для работы привязки "основной — подробности" необходимо, чтобы привязка привязывается к свойству Orders в классе Customers, а не к отдельному узлу Orders. Обратите внимание на приведенную ниже иллюстрацию. Перетащите свойство Orders класса Customers в нижнюю половину формы, чтобы конструктор поместит его в строку 2:

     ![Перетаскивание классов Orders в виде сетки](../data-tools/media/raddata-drag-orders-classes-as-grid.png "раддата. Перетаскивание классов Orders AS Grid")

7. Visual Studio создала весь код привязки, который подключает элементы управления пользовательского интерфейса к событиям в модели. Все, что нужно сделать, чтобы увидеть некоторые данные, — написать код для заполнения модели. Сначала давайте переходим к MainWindow.xaml.cs и добавим член данных в класс MainWindow для контекста данных. Этот объект, который был создан для нас, действует примерно так же, как элемент управления, отслеживающий изменения и события в модели. Пока мы добавим два члена, которые будут использоваться позже для добавления нового клиента или нового заказа. Мы также добавим логику инициализации конструктора. Начало нашего класса должно выглядеть следующим образом:

    ```csharp
    public partial class MainWindow : Window
       {
           public Customer newCustomer { get; set; }
           public Order newOrder { get; set; }

           NorthwindEntities context = new NorthwindEntities();
           CollectionViewSource custViewSource;
           CollectionViewSource ordViewSource;

           public MainWindow()
           {
               InitializeComponent();
               newCustomer = new Customer();
               newOrder = new Order();
               custViewSource = ((CollectionViewSource)
                   (FindResource("customerViewSource")));
               ordViewSource = ((CollectionViewSource)
                   (FindResource("customerOrdersViewSource")));
               DataContext = this;
           }
    ```

     Добавьте `using` директиву для System. Data. Entity, чтобы перевести метод расширения нагрузки в область:

    ```csharp
    using System.Data.Entity;
    ```

     Теперь прокрутите вниз и найдите обработчик событий Window_Loaded. Обратите внимание, что в Visual Studio добавлен объект CollectionViewSource для нас. Представляет объект Норсвиндентитиес, который мы выбрали при создании модели. Добавим код в Window_loaded, чтобы весь метод теперь выглядит следующим образом:

    ```csharp
    private void Window_Loaded(object sender, RoutedEventArgs e)
        {
            // Load is an extension method on IQueryable,
            // defined in the System.Data.Entity namespace.
            // This method enumerates the results of the query,
            // similar to ToList but without creating a list.
            // When used with Linq to Entities this method
            // creates entity objects and adds them to the context.
            context.Customers.Load();

            // After the data is loaded call the DbSet<T>.Local property
            // to use the DbSet<T> as a binding source.
            custViewSource.Source = context.Customers.Local;
        }
    ```

8. Нажмите клавишу **F5**. Вы должны увидеть сведения для первого клиента, полученного в CollectionViewSource, и их заказы в сетке данных. Форматирование не имеет ничего хорошего, так что давайте исправляется. и можно создавать способы просмотра других записей и выполнять базовые операции CRUD.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Настройка макета страницы и добавление сеток для новых клиентов и заказов
 Расположение по умолчанию, созданное Visual Studio, не идеально подходит для нашего приложения, поэтому мы сделаем некоторые изменения вручную в XAML. Кроме того, потребуются некоторые «формы» (которые являются сетками), чтобы пользователь мог добавить нового клиента или новый заказ.    Для добавления нового клиента и заказа необходим отдельный набор текстовых полей, которые не привязаны к данным `CollectionViewSource` . Мы будем контролировать, какую сетку пользователь видит в любое заданное время, установив свойство Visible в методах обработчика.

 Наконец, мы добавим кнопку DELETE к каждой строке в сетке заказы, чтобы позволить пользователю удалить отдельный заказ.

 Сначала добавьте эти стили в Windows. Resources:

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

 Затем замените всю внешнюю сетку этой разметкой:

```xaml
<Grid >
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
         <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />
         <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
         <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>
         <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
         <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
         <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
         <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
         <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
         <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
     </StackPanel>
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
         <TextBox x:Name="customerIDTextBox"  Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>
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
         <TextBox x:Name="add_customerIDTextBox"  Grid.Row="0"  Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>
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
                         <Button Content="Delete"  Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
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

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Добавление кнопок для навигации, добавления, обновления и удаления
 В Windows Forms приложениях вы получаете объект BindingNavigator с кнопками для навигации по строкам в базе данных и выполнения базовых операций CRUD. WPF не предоставляет BindingNavigator, но они достаточно просты для выполнения. Мы сделаем это с помощью кнопок в горизонтальной StackPanel в нижней строке сетки страницы, и мы будем связывать кнопки с командами, привязанными к методам в коде программной части.

 Логика команды состоит из четырех частей: (1) команды, (2) привязки, (3) кнопки и (4) обработчики команд в коде программной части.

#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Добавление команд, привязок и кнопок в XAML

1. Сначала добавим команды в наш файл MainWindow. XAML внутри элемента Windows. Resources:

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

2. CommandBinding сопоставляет событие RoutedUICommand с методом в коде программной части. Добавьте этот элемент CommandBindings после закрывающего тега Windows. Resources:

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

3. Теперь добавим StackPanel с кнопками навигации, добавления, удаления и обновления. Сначала добавьте этот стиль в Windows. Resources:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Теперь вставьте этот код сразу после RowDefinitions для внешнего элемента Grid в верхнюю часть страницы XAML:

    ```xaml
    <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />
        <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>
        <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Добавление обработчиков команд в класс MainWindow

1. Код программной части является минимальным, за исключением методов Add и DELETE. Обратите внимание, что Навигация выполняется путем вызова методов для свойства View объекта CollectionViewSource. В Делетеордеркоммандхандлер показано, как выполнить каскадное удаление в заказе. Сначала необходимо удалить связанные с ним Order_Details. Упдатекоммандхандлер добавляет нового клиента в коллекцию или просто обновляет существующий объект любыми изменениями, внесенными пользователем в текстовых полях.

2. Добавьте эти методы обработчика в класс MainWindow в MainWindow.xaml.cs, если CollectionViewSource для таблицы Customers имеет другое имя, необходимо изменить имя в каждом из этих методов:

    ```csharp
       private void LastCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToLast();
    }

    private void PreviousCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToPrevious();
    }

    private void NextCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToNext();
    }

    private void FirstCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToFirst();
    }

    private void DeleteCustomerCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        // If existing window is visible, then delete the customer and all their orders.
        // In a real application, you should add warnings and allow a user to cancel the operation.
        var cur = custViewSource.View.CurrentItem as Customer;

        var cust = (from c in context.Customers
                    where c.CustomerID == cur.CustomerID
                    select c).FirstOrDefault();

        if (cust != null)
        {
            foreach (var ord in cust.Orders.ToList())
            {
                Delete_Order(ord);
            }
            context.Customers.Remove(cust);
        }
        context.SaveChanges();
        custViewSource.View.Refresh();
    }

    // Commit changes from the new customer form, the new order form,
    // or edits made to the existing customer form.
    private void UpdateCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        if (newCustomerGrid.IsVisible)
        {
            // Create a new object because the old one
            // is being tracked by EF now.
            newCustomer = new Customer();
            newCustomer.Address = add_addressTextBox.Text;
            newCustomer.City = add_cityTextBox.Text;
            newCustomer.CompanyName = add_companyNameTextBox.Text;
            newCustomer.ContactName = add_contactNameTextBox.Text;
            newCustomer.ContactTitle = add_contactTitleTextBox.Text;
            newCustomer.Country = add_countryTextBox.Text;
            newCustomer.CustomerID = add_customerIDTextBox.Text;
            newCustomer.Fax = add_faxTextBox.Text;
            newCustomer.Phone = add_phoneTextBox.Text;
            newCustomer.PostalCode = add_postalCodeTextBox.Text;
            newCustomer.Region = add_regionTextBox.Text;

            // Perform very basic validation
            if (newCustomer.CustomerID.Length == 5)
            {
                // Insert the new customer at correct position:
                int len = context.Customers.Local.Count();
                int pos = len;
                for (int i = 0; i < len; ++i)
                {
                    if (String.CompareOrdinal(newCustomer.CustomerID, context.Customers.Local[i].CustomerID) < 0)
                    {
                        pos = i;
                        break;
                    }
                }
                context.Customers.Local.Insert(pos, newCustomer);
                custViewSource.View.Refresh();
                custViewSource.View.MoveCurrentTo(newCustomer);
            }
            else
            {
                MessageBox.Show("CustomerID must have 5 characters.");
            }

            newCustomerGrid.Visibility = Visibility.Collapsed;
            existingCustomerGrid.Visibility = Visibility.Visible;
        }
        else if (newOrderGrid.IsVisible)
        {
            // Order ID is auto-generated so we don't set it here.
            // For CustomerID, address, etc we use the values from current customer.
            // User can modify these in the datagrid after the order is entered.

            newOrder.OrderDate = add_orderDatePicker.SelectedDate;
            newOrder.RequiredDate = add_requiredDatePicker.SelectedDate;
            newOrder.ShippedDate = add_shippedDatePicker.SelectedDate;
            try
            {
                // Exercise for the reader if you are using Northwind:
                // Add the Northwind Shippers table to the model.
                // Acceptable ShipperID values are 1, 2, or 3.
                if (add_ShipViaTextBox.Text == "1" || add_ShipViaTextBox.Text == "2"
                    || add_ShipViaTextBox.Text == "3")
                {
                    newOrder.ShipVia = Convert.ToInt32(add_ShipViaTextBox.Text);
                }
                else
                {
                    MessageBox.Show("Shipper ID must be 1, 2, or 3 in Northwind.");
                    return;
                }
            }
            catch
            {
                MessageBox.Show("Ship Via must be convertible to int");
                return;
            }
            try
            {
                newOrder.Freight = Convert.ToDecimal(add_freightTextBox.Text);
            }
            catch
            {
                MessageBox.Show("Freight must be convertible to decimal.");
                return;
            }

            // Add the order into the EF model
            context.Orders.Add(newOrder);
            ordViewSource.View.Refresh();
        }

        // Save the changes, either for a new customer, a new order
        // or an edit in an existing customer or order
        context.SaveChanges();
    }

    // Sets up the form so that user can enter data. Data is later
    // saved when user clicks Commit.
    private void AddCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        existingCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.Visibility = Visibility.Collapsed;
        newCustomerGrid.Visibility = Visibility.Visible;

        // Clear all the text boxes before adding a new customer.
        foreach (var child in newCustomerGrid.Children)
        {
            var tb = child as TextBox;
            if (tb != null)
            {
                tb.Text = "";
            }
        }
    }

    private void NewOrder_click(object sender, RoutedEventArgs e)
    {
        var cust = custViewSource.View.CurrentItem as Customer;
        if (cust == null)
        {
            MessageBox.Show("No customer selected.");
            return;
        }

        newOrder.CustomerID = cust.CustomerID;

        // Get address and other mostly constant fields from
        // an existing order, if one exists
        var coll = custViewSource.Source as IEnumerable<Customer>;
        var lastOrder = (from c in coll
                         from ord in c.Orders
                         select ord).LastOrDefault();
        if (lastOrder != null)
        {
            newOrder.ShipAddress = lastOrder.ShipAddress;
            newOrder.ShipCity = lastOrder.ShipCity;
            newOrder.ShipCountry = lastOrder.ShipCountry;
            newOrder.ShipName = lastOrder.ShipName;
            newOrder.ShipPostalCode = lastOrder.ShipPostalCode;
            newOrder.ShipRegion = lastOrder.ShipRegion;
        }

        existingCustomerGrid.Visibility = Visibility.Collapsed;
        newCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.UpdateLayout();
        newOrderGrid.Visibility = Visibility.Visible;
    }

    // Cancels any input into the new customer form
    private void CancelCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        add_addressTextBox.Text = "";
        add_cityTextBox.Text = "";
        add_companyNameTextBox.Text = "";
        add_contactNameTextBox.Text = "";
        add_contactTitleTextBox.Text = "";
        add_countryTextBox.Text = "";
        add_customerIDTextBox.Text = "";
        add_faxTextBox.Text = "";
        add_phoneTextBox.Text = "";
        add_postalCodeTextBox.Text = "";
        add_regionTextBox.Text = "";

        existingCustomerGrid.Visibility = Visibility.Visible;
        newCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.Visibility = Visibility.Collapsed;
    }

    private void Delete_Order(Order order)
    {
        // Find the order in the EF model.
        var ord = (from o in context.Orders.Local
                   where o.OrderID == order.OrderID
                   select o).FirstOrDefault();

        // Delete all the order_details that have
        // this Order as a foreign key
        foreach (var detail in ord.Order_Details.ToList())
        {
            context.Order_Details.Remove(detail);
        }

        // Now it's safe to delete the order.
        context.Orders.Remove(ord);
        context.SaveChanges();

        // Update the data grid.
        ordViewSource.View.Refresh();
    }

    private void DeleteOrderCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        // Get the Order in the row in which the Delete button was clicked.
        Order obj = e.Parameter as Order;
        Delete_Order(obj);
    }
    ```

3. Нажмите клавишу **F5**. Вы должны увидеть данные, и кнопки навигации должны работать надлежащим образом. Щелкните "фиксация", чтобы добавить нового клиента или заказ в модель после того, как вы введете данные.  Щелкните "Отмена" для выхода из нового клиента или новой формы заказа без сохранения. Вы можете вносить изменения в существующие клиенты и заказы непосредственно в текстовые поля, и эти изменения будут автоматически записываться в модель.

## <a name="see-also"></a>См. также:
 [Документация по](https://msdn.microsoft.com/data/ee712907.aspx) [средствам Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) Entity Framework
