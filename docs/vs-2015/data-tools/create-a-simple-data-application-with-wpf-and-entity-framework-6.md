---
title: Создание простых данных приложения с помощью WPF и Entity Framework 6 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 62e1a6c317752dc5513a51d3e8018d15c9598b93
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664804"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Создание простого приложения для обработки данных с помощью WPF и Entity Framework 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Этом пошаговом руководстве показано, как создать приложение основные «формы поверх данных» в Visual Studio с помощью SQL Server LocalDB, базы данных "Борей", Entity Framework 6 и Windows Presentation Foundation. Показано, как выполнять основные привязку данных с основного / подробного представления, и она также содержит настраиваемые «привязка навигатора» с помощью кнопок «Переместить вперед», «Переместить назад,» «Перейти к началу,» «переместить в конец,» «Обновить» и «Удалить».  
  
 В этой статье рассматривается использование средства данных в Visual Studio и не будет пытаться объяснить базовых технологий в любой глубины. Предполагается, что у вас есть базовые знания о XAML, Entity Framework и SQL. В этом примере также показано архитектуре MVVM, которые являются стандартными для приложений WPF. Тем не менее можно скопировать этот код в приложение MVVM с очень небольшими изменениями.  
  
## <a name="install-and-connect-to-northwind"></a>Установка и подключение к "Борей"  
 В этом примере используется SQL Server Express LocalDB и базе данных Northwind. Он должен работать с другими продуктами баз данных SQL так же хорошо, если платформа Entity Framework поддерживает поставщик данных ADO.NET для этого продукта.  
  
1.  Если это еще не сделано, установите SQL Server 2014 LocalDB Express 32-разрядный из [странице скачивания выпуски SQL Server](https://www.microsoft.com/sql-server/sql-server-editions-express).  
  
2.  Установка образца базы данных "Борей", следуя приведенным ниже указаниям: [Установка образцов баз данных SQL Server](../data-tools/install-sql-server-sample-databases.md).  
  
3.  [Добавление новых подключений](../data-tools/add-new-connections.md) для Northwind.  
  
## <a name="configure-the-project"></a>Настройка проекта  
  
1.  В Visual Studio, выберите **файл &#124; новый проект** и создайте новое приложение WPF C#.  
  
2.  Далее мы добавим пакет NuGet для платформы Entity Framework 6. В обозревателе решений выберите узел проекта. В главном меню выберите **проекта &#124; управление пакетами NuGet...**  
  
     ![Управление пакетами NuGet пункта меню](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")  
  
3.  В диспетчере пакетов NuGet, щелкните **Обзор** ссылку. Entity Framework, вероятно, является верхний пакет в списке. Нажмите кнопку **установить** в правой области и следуйте инструкциям на экране. В окне вывода о том, когда установка будет завершена.  
  
     ![Пакет NuGet Entity Framework](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")  
  
4.  Теперь можно использовать Visual Studio для создания модели на основе базы данных "Борей".  
  
## <a name="create-the-model"></a>Создание модели  
  
1. Щелкните правой кнопкой узел проекта в обозревателе решений и выберите **добавить &#124; новый элемент**. В левой области, в узле C# выберите **данных** и в средней области выберите **ADO.NET Entity Data Model**.  
  
    ![Новый элемент проекта Entity Framework модель](../data-tools/media/raddata-ef-new-project-item.png "raddata EF нового элемента проекта")  
  
2. Вызов ее `Northwind_model` и нажмите кнопку ОК. Откроется **мастер моделей EDM**. Выберите **конструктор EF из базы данных** и нажмите кнопку **Далее**.  
  
    ![Модель EF из базы данных](../data-tools/media/raddata-ef-model-from-database.png "raddata модель EF из базы данных")  
  
3. На следующем экране выберите ваш LocalDB Northwind, соединения и нажмите **Далее**.  
  
4. На следующей странице мастера выберите, какие таблицы, хранимые процедуры и другие объекты базы данных для включения в модель Entity Framework. Разверните узел dbo в представлении в виде дерева и выберите клиенты, заказы и сведения о заказе. Оставьте значения по умолчанию флажок установлен и нажмите кнопку **Готово**.  
  
    ![Выбор объектов базы данных для модели](../data-tools/media/raddata-choose-ef-objects.png "raddata Выбор объектов EF")  
  
5. Мастер формирует классы C#, которые представляют модель Entity Framework. Это обычный старый классы C# и их мы будет databind для пользовательского интерфейса WPF. EDMX-файл описывает связи и другие метаданные, который связывает классы с объектами в базе данных.  TT-файлов, шаблонов T4 для создания кода, которые будут работать на модели и сохранить изменения в базе данных. Вы увидите все эти файлы в обозревателе решений в узле Northwind_model:  
  
    ![Файлы модели EF в обозревателе решений](../data-tools/media/raddata-solution-explorer-ef-model-files.png "файлов модели raddata EF обозревателя решений")  
  
    Область конструктора для EDMX-файл можно изменить некоторые свойства и отношения в модели. Мы не будем использовать конструктор в этом пошаговом руководстве.  
  
6. TT-файлов общего назначения, и нам нужно настроить один из них для работы с привязка данных WPF, который требует ObservableCollections.  В обозревателе решений разверните узел Northwind_model, пока не найдете Northwind_model.tt. (Убедитесь, что вы являетесь **не** в *. Контекст tt-файла он непосредственно меньше EDMX-файл).  
  
   -   Заменить два вхождения <xref:System.Collections.ICollection> с <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
   -   Замените первое вхождение <xref:System.Collections.Generic.HashSet%601> с <xref:System.Collections.ObjectModel.ObservableCollection%601> около строки 51. Не заменяйте второе вхождение HashSet  
  
   -   Замените только вхождение <xref:System.Collections.Generic> (около строки 334) с <xref:System.Collections.ObjectModel>.  
  
7. Нажмите клавишу **Ctrl + Shift + B** для сборки проекта. После завершения построения, классы моделей являются видимыми для мастера источников данных.  
  
   Теперь мы готовы для подключения этой модели на страницу XAML, что мы просматривать, перемещения и изменения данных.  
  
## <a name="databind-the-model-to-the-xaml-page"></a>DataBind модели на страницу XAML  
 Можно написать собственный код привязки данных, но гораздо проще позволить Visual Studio сделаем это за вас.  
  
1.  В главном меню выберите **проекта &#124; добавить новый источник данных** откроется **мастер настройки источника данных**. Выберите **объект** так, как выполняется привязка к классам модели, не к базе данных:  
  
     ![Мастер настройки источника данных с источника объекта](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata мастер настройки источника данных с источника объекта")  
  
2.  Выберите клиента.  (Источников для заказов создается автоматически из свойства навигации заказов клиента.)  
  
     ![Добавьте классы сущностей в качестве источников данных](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "классы raddata добавить сущность в качестве источников данных")  
  
3.  Нажмите кнопку **Готово**  
  
4.  Перейдите на файл MainWindow.xaml в представлении кода. Мы собираемся поддерживать очень простое XAML для целей этого примера. Изменение заголовка MainWindow на более описательное и увеличьте его высоту и ширину для 600 x 800 сейчас. Ее можно всегда изменить позже. Теперь добавьте следующие определения три строки в основной сетке одну строку для кнопок навигации, один для сведений о клиенте, один для сетку, которая отображает заказы:  
  
    ```xaml  
    <Grid.RowDefinitions>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="*"/>  
           </Grid.RowDefinitions>  
    ```  
  
5.  Теперь откройте файл MainWindow.xaml, чтобы просмотреть его в конструкторе. В результате окна «Источники данных» отображается как параметр в поле окна Visual Studio рядом с панели элементов. Перейдите на вкладку, чтобы открыть окно, или в противном случае щелкните **Shift + Alt + D** или выберите **представление &#124; Other Windows &#124; источников данных**. Мы собираемся отображения каждого свойства в классе клиентов в собственном окне отдельного фрагмента текста. Во-первых, щелкните стрелку в поле со списком клиентов и выберите пункт **сведения**. Затем перетащите узел в средней части области конструктора, чтобы конструктор знает, что необходимо перейти в среднюю строку.  Если вы потеряли его, можно указать строку вручную в XAML. По умолчанию элементы управления размещаются по вертикали в элемента сетки, но на этом этапе можно упорядочивать их как вам нравится в форме.  Например смысл поместить поле в верхней части, выше адрес. Пример приложения для этой статьи изменяет порядок полей и размещает их на два столбца.  
  
     ![Привязку к источнику данных клиентов на отдельные элементы управления](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "привязку к источнику данных raddata клиентов на отдельные элементы управления")  
  
     В представлении кода вы увидите новый `Grid` элементу в строке 1 (посередине) родительского элемента сетки. Сетка содержит родительский `DataContext` атрибут, который относится к CollectionViewSource, который был добавлен `Windows.Resources` элемент. Учитывая этот контекст данных, если первое текстовое поле, например, привязывается к @ i «Address» это имя сопоставляется `Address` свойств в текущем `Customer` объекта в CollectionViewSource.  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  
  
6.  Клиент отображается в верхней части окна, мы хотим для просмотра заказов в нижней половине. Мы покажем заказы в элементе управления представления одной ячейке сетки. Для привязки данных основной / подробности работала должным образом очень важно, выполняется привязка к свойству Orders в классе клиентов не на отдельном узле заказов. Обратите внимание на следующей иллюстрации! Перетащите свойство Orders класса клиентов в нижней области формы, таким образом, чтобы, конструктор поместит его в строке 2:  
  
     ![Перетащить классы заказов в виде сетки](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata заказы перетащите классы в виде сетки")  
  
7.  Visual Studio создала весь код привязки, который подключается к событиям модели элементов управления пользовательского интерфейса. Все, что нам нужно выполнить, чтобы просмотреть некоторые данные, является написание кода для заполнения модели. Первый давайте перейдите к MainWindow.xaml.cs и добавьте данные-член к классу MainWindow для контекста данных. Этот объект, который был создан для нас, действует примерно элемент управления, который отслеживает изменения и другие события в модели. Хотя мы здесь, мы добавим два члена, которые мы будем использовать для добавления нового клиента или нового заказа. Также мы добавим логику инициализации конструктора. Вверху наш класс должен выглядеть следующим образом:  
  
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
  
     Добавление `using` директив для System.Data.Entity для вызова метода расширения Load в область действия:  
  
    ```csharp  
    using System.Data.Entity;  
    ```  
  
     Теперь прокрутите вниз и найдите Window_Loaded обработчик событий. Обратите внимание на то, что Visual Studio добавляет объект CollectionViewSource для нас. Представляет объект NorthwindEntities, который мы выбрали при создании модели. Давайте добавим код, Window_loaded таким образом, чтобы весь метод теперь выглядит следующим образом:  
  
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
  
8.  Нажмите клавишу **F5**. Вы увидите сведения для первого клиента, который был извлечен в CollectionViewSource и их заказы в сетке данных. Форматирование не слишком подробная, так что давайте исправим ее. создать механизм для просмотра других записей и выполнять основные операции CRUD.  
  
## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Изменить макет страницы и добавление сеток для новых клиентов и заказы  
 Расположение по умолчанию, созданные Visual Studio не идеально подходят для нашего приложения, поэтому мы внесем некоторые изменения вручную в XAML. Мы также потребуется некоторые «формы» (которые фактически сетки) позволяют пользователю для добавления нового клиента или нового заказа.    Чтобы иметь возможность добавлять новый customer и order, полностью отдельный набор текстовых полей, которые не привязаны к `CollectionViewSource`. Мы будем контролировать какие сетки, пользователь видит в любой момент времени, задав свойство Visible в методы обработчика.  
  
 Наконец мы добавим кнопку «Удалить» для каждой строки в таблице заказов, чтобы пользователь мог удалить отдельного заказа.  
  
 Во-первых добавьте эти стили Windows.Resources:  
  
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
  
## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Добавление кнопок для перехода, добавление, обновление и удаление  
 В приложениях Windows Forms вы получите объект BindingNavigator с кнопками для просмотра строк в базе данных и выполнение основных операций CRUD. WPF предоставляет BindingNavigator, но они являются довольно легко сделать. Это необходимо сделать с помощью кнопок в StackPanel по горизонтали в нижней строке сетки на страницы, и мы свяжем кнопок с командами, которые привязаны к методам в коде программной части.  
  
 Существует части четверки логику команды: (1) команды, (2 привязки, (3) кнопок и (4) обработчиками команд в код программной части.  
  
#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Добавление команд, привязок и кнопок в XAML  
  
1.  Во-первых добавим в наш файл MainWindow.XAML внутри элемента Windows.Resources команды:  
  
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
  
2.  CommandBinding сопоставляет события RoutedUICommand метод в коде программной части. Добавьте этот элемент CommandBindings после Windows.Resources, закрывающий тег:  
  
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
  
3.  Теперь давайте добавить StackPanel с панели навигации, добавлять, удалять и обновлять кнопок. Во-первых добавьте этот стиль Windows.Resources:  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     Теперь вставьте этот код сразу после RowDefinitions для внешнего элемента сетки, в верхней части страницы XAML:  
  
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
  
#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Добавьте в класс MainWindow обработчиков команд  
  
1.  Код программной части сводится к минимуму, за исключением методы добавления и удаления. Обратите внимание на то, что переход выполняется путем вызова методов на свойство представления CollectionViewSource. DeleteOrderCommandHandler показано, как провести каскадное удаление заказа. Нам нужно сначала удалить данные заказа, связанные с ним. UpdateCommandHandler добавляет к коллекции нового клиента, в противном случае просто обновляет существующий объект все, что изменения пользователя, внесенные в текстовых полях.  
  
2.  Добавьте эти методы обработчика класса MainWindow в файле MainWindow.xaml.cs, если ваш CollectionViewSource для таблицы Customers имеет другое имя, необходимо изменить имя в каждом из этих методов:  
  
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
  
3.  Нажмите клавишу **F5**. Вы должны увидеть ваши данные и кнопки навигации должен работать соответствующим образом. Щелкните «Фиксации», чтобы добавить нового клиента или заказа в модель, после ввода данных.  Щелкните «Отмена», чтобы восстановить новой формы или нового заказа клиента без сохранения. Можно вносить изменения в существующие клиенты и заказы непосредственно в текстовые поля, и эти изменения будут записаны в модель автоматически.  
  
## <a name="see-also"></a>См. также  
 [Visual Studio data tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [документация по Entity Framework](https://msdn.microsoft.com/data/ee712907.aspx)
