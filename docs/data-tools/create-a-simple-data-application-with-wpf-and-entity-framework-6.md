---
title: "Создание простых данных приложения с помощью WPF и Entity Framework 6 | Документы Microsoft"
ms.custom: 
ms.date: 08/22/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: c4dd77680fb529575140dc718a4f1c0a58090029
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Создание простых данных приложения с помощью WPF и Entity Framework 6
Этот walkthough показано, как создать приложение основные» форм на основе данных» в Visual Studio с SQL Server LocalDB, базы данных Northwind, Entity Framework 6 и Windows Presentation Foundation. Показано, как выполнять основные привязки данных с представлением основной подробности, а также имеет пользовательские «привязка навигатор» с кнопками «Переместить следующий», «Переместить предыдущий, ««Переместить в начало,» «переместить в конец,» «Обновить» и «Delete».  
  
 В этой статье основное внимание уделяется средствами данных в Visual Studio и не будет пытаться объяснить базовых технологий в любой глубины. Предполагается, что имеется Знакомство с XAML, Entity Framework и SQL. В этом примере также показаны не архитектуры Model-View-View Model (MVVM), которая является стандартным для приложений WPF. Тем не менее можно скопировать этот код в собственное приложение MVVM незначительных изменений.  
  
## <a name="install-and-connect-to-northwind"></a>Установка и подключение к Northwind  
В этом примере используется SQL Server Express LocalDB и базе данных Northwind. Она должна работать с другими продуктами SQL базы данных точно так же, если Entity Framework поддерживает поставщик данных ADO.NET для этого продукта.  
  
1.  Если у вас нет SQL Server Express LocalDB, установите его из [страница загрузки выпуски SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), либо с помощью **установщик Visual Studio**. Установщик Visual Studio можно установить SQL Server Express LocalDB в рамках **разработки настольных приложений .NET** рабочей нагрузки, или в отдельных компонентов.  
  
2.  Установка образца базы данных Northwind, выполните следующие действия:  

    1. В Visual Studio откройте **обозреватель объектов SQL Server** окна. (Обозреватель объектов SQL Server устанавливается как часть **хранения и обработки данных** рабочей нагрузки в установщик Visual Studio.) Разверните **SQL Server** узла. Щелкните правой кнопкой мыши на экземпляре LocalDB и выберите **нового запроса...** .  

       Откроется окно редактора запросов.  

    2. Копировать [сценарий Northwind Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот скрипт T-SQL создает базу данных Northwind с нуля и заполняет ее данными.  

    3. Вставьте скрипт T-SQL в редакторе запросов, а затем выберите **Execute** кнопки.  

       Через некоторое время завершения выполнения запроса и создания базы данных "Борей".  
  
3.  [Добавление новых подключений](../data-tools/add-new-connections.md) для Northwind.  
  
## <a name="configure-the-project"></a>Настройка проекта  
  
1.  В Visual Studio выберите **файл**, **New**, **проекта...**  и создайте новое приложение WPF C#.  
  
2.  Далее мы добавим пакета NuGet для платформы Entity Framework 6. В обозревателе решений выберите узел проекта. В главном меню выберите **проекта**, **управление пакетами NuGet...**  
  
     ![Управление пакетами NuGet пункта меню](../data-tools/media/raddata_vs2015_manage_nuget_packages.png "raddata_vs2015_manage_nuget_packages")  
  
3.  В диспетчере пакетов NuGet, нажмите кнопку **Обзор** ссылку. Entity Framework, скорее всего, является верхней пакета в списке. Нажмите кнопку **установить** в правой области и следуйте инструкциям на экране. В окне вывода сообщает о завершении установки.  
  
     ![Пакет NuGet Entity Framework](../data-tools/media/raddata_vs2015_nuget_ef.png "raddata_vs2015_Nuget_EF")  
  
4.  Теперь можно использовать Visual Studio для создания модели, основанной на базе данных Northwind.  
  
## <a name="create-the-model"></a>Создание модели  
  
1.  Щелкните правой кнопкой мыши узел проекта в обозревателе решений и выберите **добавить**, **новый элемент...** . В левой области разверните узел C# и выберите **данные** и в средней области выберите **ADO.NET Entity Data Model**.  
  
     ![Новый элемент проекта Entity Framework модель](../data-tools/media/raddata-ef-new-project-item.png "raddata EF нового элемента проекта")  

  2.  Вызов модели `Northwind_model` и нажмите кнопку ОК. Откроется окно **мастер моделей EDM**. Выберите **конструктор EF из базы данных** и нажмите кнопку **Далее**.  
  
     ![Модель EF из базы данных](../data-tools/media/raddata-ef-model-from-database.png "raddata модели EF из базы данных")  
  
3.  На следующем экране выберите ваш LocalDB Northwind соединения и нажмите **Далее**.  
  
4.  На следующей странице мастера выберите, какие таблицы, хранимые процедуры и другие объекты базы данных для включения в модель Entity Framework. Разверните узел dbo в представлении в виде дерева и выберите клиентов, заказов и сведения о заказе. Оставьте значения по умолчанию этот флажок установлен и нажмите кнопку **Готово**.  
  
     ![Выберите объекты базы данных для модели](../data-tools/media/raddata-choose-ef-objects.png "raddata Выбор EF объектов")  
  
5.  Мастер формирует классов C#, которые представляют модель Entity Framework. Эти простых старых классов C#, они являются мы и сделаем databind в пользовательский интерфейс WPF. EDMX-файл описывает связи и другие метаданные, связывающие классы с объектами в базе данных.  TT-файлы — это шаблоны T4, для создания кода, будут работать с моделью и сохранять изменения в базе данных. Вы увидите все эти файлы в обозревателе решений в узле Northwind_model:  

       ![Файлы модели EF обозревателя решений](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata файлы модели EF обозревателя решений")  
  
     Область конструктора для EDMX-файла можно изменить некоторые свойства и связи в модели. Мы не будем использования конструктора в этом пошаговом руководстве.  
  
6.  TT-файлы являются общего назначения, и нам необходимо настроить один из них для работы с WPF привязку данных, которая требует ObservableCollections.  В обозревателе решений разверните узел Northwind_model, пока не найдете Northwind_model.tt. (Убедитесь, что вы являетесь **не** в *. Контекст tt-файл это непосредственно ниже EDMX-файл).  
  
    -   Заменить два вхождения <xref:System.Collections.ICollection> с <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
    -   Замените на первое вхождение <xref:System.Collections.Generic.HashSet%601> с <xref:System.Collections.ObjectModel.ObservableCollection%601> около строки 51. Не заменяйте второго вхождения HashSet  
  
    -   Замените только вхождения <xref:System.Collections.Generic> (около строки 431) с <xref:System.Collections.ObjectModel>.  
  
7.  Нажмите клавишу **Ctrl + Shift + B** для сборки проекта. После завершения построения, классы модели становятся видимыми для мастера источников данных.  
  
Теперь мы готовы подключить эту модель в XAML-страницы, чтобы мы просмотра, перемещения и изменения данных.  
  
## <a name="databind-the-model-to-the-xaml-page"></a>Привязки модели для XAML-страницы  
 Можно написать собственный код привязки данных, но это гораздо проще сделать это для вас Visual Studio.  
  
1.  В главном меню выберите **проект > Добавить новый источник данных** для вызова **мастер настройки источника данных**. Выберите **объекта** , так как выполняется привязка к классам модели, не в базу данных:  
  
     ![Мастер настройки источника данных с исходного объекта](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata мастер настройки источника данных с исходного объекта")  
  
2.  Выберите клиента.  (Источники для заказов будет автоматически создан из свойства навигации заказов клиента.)  
  
     ![Добавьте классы сущностей в качестве источников данных](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "классы raddata добавить сущность в качестве источников данных")  
  
3.  Нажмите кнопку **Готово**  
  
4.  Откройте файл MainWindow.xaml в представлении кода. Мы будем хранить очень простой XAML для целей этого примера. Изменение названия MainWindow более подробным и повысить его высота и ширина 600 x 800 сейчас. Его можно всегда изменить позже. Теперь добавьте следующие три строки определения в основной сетке одну строку для кнопок навигации, один для сведения о клиенте, один для сетки, которая показывает количество заявок на их:  

    ```xaml  
    <Grid.RowDefinitions>  
            <RowDefinition Height="auto"/>  
            <RowDefinition Height="auto"/>  
            <RowDefinition Height="*"/>  
        </Grid.RowDefinitions>
    ```

5.  Теперь откройте файл MainWindow.xaml, чтобы вы просматриваете в конструкторе. В результате окна источников данных для отображения в качестве параметра в Visual Studio окно границу рядом с панели элементов. Щелкните вкладку, чтобы открыть окно или в противном случае щелкните **Shift + Alt + D** или выберите **представление &#124; Другие окна &#124; Источники данных**. Мы собираемся отображения каждого свойства в классе клиентов в свой собственный отдельного текстового поля. Сначала щелкните стрелку в поле со списком клиентов и выберите **сведения**. Затем перетащите узел в средней части рабочей области конструктора, чтобы конструктор знает, что необходимо перейти в середине строки.  Если вы потеряли его, можно указать строку вручную позднее в XAML. По умолчанию элементы управления по вертикали помещаются в элемент сетки, но в этот момент можно упорядочить их следования в форме.  Например он может быть целесообразно поместить поле в верхней части выше адрес. Образец приложения для данной статьи изменить порядок полей и упорядочивает их на два столбца.  
  
     ![Привязка источника данных клиентов на отдельные элементы управления](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "raddata клиентов привязки источника данных на отдельные элементы управления")  
  
     В представлении кода, теперь можно увидеть новый `Grid` дочерним для элемента первой строки (посередине) сетки. Сетка содержит родительский `DataContext` атрибут, который ссылается на CollectionViewSource, который будет добавлен `Windows.Resources` элемента. Получает контекст данных, при первом текстовое поле, например, привязки для этого имени «Address» сопоставляется `Address` свойство в текущем `Customer` объекта в CollectionViewSource.  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  

6.  Клиент отображается в верхней части окна, мы хотим увидеть их заказы в нижней половине. Мы покажем заказы в одной ячейке сетки элемента управления представления. Для основной подробности привязки данных для правильной работы важно выполняется привязка к свойству "Orders" в классе клиентов не на отдельном узле заказов. Обратите внимание на следующем рисунке. Перетащите свойство заказы клиентов класса в нижней части формы, таким образом, чтобы конструктор помещает его в строку 2:  
  
     ![Перетащите заказов классы как сетка](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata заказы перетащите классы как сетка")  
  
7.  Visual Studio создала все привязки код, который подключается к событиям модели элементов управления пользовательского интерфейса. Все, что нам нужно, чтобы видеть некоторые данные, требуется написать код для заполнения модели. Первый давайте перейдите к MainWindow.xaml.cs и добавьте данные-член класса MainWindow для контекста данных. Этот объект, который был создан для нас, действует нечто похожее на элемент управления, который отслеживает изменения и событий в модели. Кроме того, мы добавим логику инициализации конструктора. Начало нашей класса должно выглядеть следующим образом:  
  
     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]  
     
     Добавить `using` директивы System.Data.Entity для добавления в область видимости метод расширения нагрузки:  
  
     ```csharp
     using System.Data.Entity;  
     ```  

     Теперь прокрутите вниз и найдите Window_Loaded обработчик события. Обратите внимание, что среда Visual Studio добавила нам объекта CollectionViewSource. Представляет объект NorthwindEntities, который мы выбрали создания модели. Давайте добавим код Window_Loaded, чтобы весь метод теперь выглядит следующим образом:  

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]  

8.  Нажмите клавишу **F5**. Вы увидите подробные сведения для первого клиента, который был извлечен в CollectionViewSource. Вы также увидите их заказы в сетке данных. Форматирование не большие, так что давайте решить эту проблему. Также мы создадим такую возможность просматривать другие записи и выполнять основные операции CRUD.  
  
## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Измените макет страницы и Добавление таблицы для новых клиентов и заказы  
Расположение по умолчанию, созданные Visual Studio не идеально подходит для нашего приложения, поэтому мы внесем некоторые изменения вручную в XAML. Мы также потребуется некоторых «forms» (которые фактически сетки) позволяют пользователю добавить нового клиента или заказа. Чтобы иметь возможность добавить новые customer и order, мы должны отдельный набор текстовых полей, которые не являются привязкой к данным для `CollectionViewSource`. Мы будем управления сетки, какой пользователь видит в любой момент времени, задав свойство Visible в методы обработчика. Наконец мы добавим кнопку «Удалить» для каждой строки в сетке заказов, чтобы пользователь мог удалить отдельного заказа.  
  
Во-первых добавьте следующие стили к элементу Windows.Resources в файле MainWindow.xaml:  
  
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
  
Затем замените всю таблицу внешнего Эта разметка:  
  
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
  
## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Добавить кнопки для перехода, добавление, обновление и удаление  
 В приложениях Windows Forms можно получить объект BindingNavigator с кнопками для просмотра строк в базе данных и выполнения основных операций CRUD. WPF предоставляет BindingNavigator, но очень легко создать его. Сделаем с кнопками внутри горизонтальной StackPanel и нам необходимо связать кнопок с командами, которые привязываются к методам в коде.  
  
 Существует четверки части логики команды: (1) команды, (2) привязки, (3) кнопок и (4) обработчик команды кода.  
  
#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Добавление команд, привязки и кнопки в XAML  
  
1.  Во-первых добавим в наш файл MainWindow.xaml внутри элемента Windows.Resources команды:  
  
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
  
2.  Событие RoutedUICommand CommandBinding сопоставляется метод в коде. Добавьте этот элемент поддержкой CommandBinding после Windows.Resources, закрывающий тег:  
  
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
  
     Во-вторых вставьте следующий код сразу после RowDefinitions внешнего элемента сетки, расположенной в верхней части страницы XAML:  
  
    ```xaml  
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
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
  
#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Добавьте в класс MainWindow обработчики команд  
  
Код программной части сводится к минимуму за исключением методы добавления и удаления. Навигации выполняется путем вызова методов на свойстве представление CollectionViewSource. DeleteOrderCommandHandler показано, как выполнить каскадное удаление заказа. Необходимо сначала удалить данные заказа, связанные с ним. UpdateCommandHandler добавляет к коллекции нового клиента или порядка, в противном случае просто обновляет существующего клиента или заказ изменения, внесенные пользователем в текстовых полях.  
  
Добавьте эти методы обработчика класса MainWindow в MainWindow.xaml.cs. Если ваш CollectionViewSource для таблицы Customers имеет другое имя, необходимо изменить имя в каждом из этих методов:  
  
[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]  
  
## <a name="run-the-application"></a>Запуск приложения
Чтобы начать отладку, нажмите клавишу **F5**. Вы увидите данные вставляются в сетке и кнопки навигации должен работать соответствующим образом. Щелкните «Фиксации», чтобы добавить нового клиента или заказ модели после ввода данных. Нажмите кнопку «Отмена» для резервного из нового клиента или в новую форму заказа без сохранения данных. Можно вносить изменения в существующие клиенты и заказы непосредственно в текстовые поля, и эти изменения записываются в модель автоматически.  
  
## <a name="see-also"></a>См. также
[Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)  
[Документации по Entity Framework](https://msdn.microsoft.com/en-us/data/ee712907.aspx)