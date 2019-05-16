---
title: Пошаговое руководство. Создание классического приложения WPF, подключенного к мобильной службе Azure | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8d42620f-553b-4b04-a38b-f6b306d73a50
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c3f1533df24af802ae0c9950d4765ea0a0bf04da
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693559"
---
# <a name="walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service"></a>Пошаговое руководство. Создание классического приложения WPF, подключенного к мобильной службе Azure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью платформы Windows Presentation Foundation (WPF) можно быстро создать современное классическое приложение, использующее мобильную службу Azure для хранения и предоставления данных.  
  
## <a name="Requirements"></a> Необходимые компоненты  
 Для выполнения этого пошагового руководства необходимо следующее:  
  
- Visual Studio 2015 — любая версия, поддерживающая разработку на основе WPF  
  
- Активная учетная запись Microsoft Azure  
  
    - Зарегистрировать бесплатную пробную учетную запись можно [здесь](https://azure.microsoft.com/pricing/free-trial/).  
  
    - Вы можете активировать [преимущества подписки MSDN](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F). С подпиской MSDN вы каждый месяц получаете кредиты, которые можно использовать для оплаты служб Azure.  
  
## <a name="create-a-project-and-add-references"></a>Создание проекта и добавление ссылок  
 Сначала нужно создать проект WPF и добавить пакет NuGet, позволяющий подключаться к мобильным службам Azure.  
  
#### <a name="to-create-the-project"></a>Создание проекта  
  
1. В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2. В диалоговом окне **Новый проект** разверните узел **Visual C#** или **Visual Basic** и выберите узел **Окна** , а затем разверните узел **Окна** и выберите узел **Классический рабочий стол** .  
  
3. В списке шаблонов выберите шаблон **Приложение WPF** .  
  
4. В диалоговом окне **Имя** введите `WPFQuickStart`и нажмите кнопку **ОК** .  
  
     Будет создан проект, файлы проекта добавятся в **обозреватель решений**, и откроется конструктор окна приложения по умолчанию с именем **MainWindow.xaml** .  
  
#### <a name="to-add-a-reference-to-the-windows-azure-mobile-services-sdk"></a>Добавление ссылки на пакет SDK для мобильных служб Microsoft Azure  
  
1. В **обозревателе решений**откройте контекстное меню узла **Ссылки** и выберите пункт **Управление пакетами NuGet**.  
  
2. В диалоговом окне **диспетчере пакетов NuGet**выберите поле **Поиск** и введите `mobileservices`.  
  
3. В левой области выберите **WindowsAzure.MobileServices**, а затем в правой области нажмите кнопку **Установить** .  
  
    > [!NOTE]
    > Если появится диалоговое окно **Предварительный просмотр** , изучите предлагаемые изменения, а затем нажмите кнопку **ОК** .  
  
4. В диалоговом окне **принятия условий лицензии** изучите условия, а затем примите их, нажав кнопку **Принимаю** .  
  
     Необходимые ссылки будут добавлены в **обозреватель решений**.  
  
    > [!NOTE]
    > Если вы не согласны с условиями лицензии, нажмите кнопку **Не принимаю** . При этом дальнейшее выполнение этого пошагового руководства будет невозможно.  
  
## <a name="create-the-user-interface"></a>Создание пользовательского интерфейса  
 Следующий шаг — создание пользовательского интерфейса приложения. Сначала вы создадите пользовательский элемент управления с возможностью повторного использования, который служит для отображения стандартного макета с двумя расположенными рядом областями. Вы добавите этот пользовательский элемент управления в главное окно приложения, добавите элементы управления для ввода и отображения данных, а затем напишете код для определения взаимодействия с сервером мобильной службы.  
  
#### <a name="to-add-a-user-control"></a>Добавление пользовательского элемента управления  
  
1. В **обозревателе решений**в контекстном меню узла **WPFQuickStart** выберите **Добавить**, **Новая папка**.  
  
2. Назовите папку `Common`.  
  
3. Откройте контекстное меню папки **Common** и выберите **Добавить**, **Пользовательский элемент управления**.  
  
4. В диалоговом окне **Добавление нового элемента** выберите поле "Имя" и введите значение `QuickStartTask`и нажмите кнопку **Добавить** .  
  
     Пользовательский элемент управления будет добавлен в проект, и в конструкторе откроется файл **QuickStartTask.xaml** .  
  
5. В нижней области конструктора выделите теги `<Grid>` и `</Grid>` и замените их следующим кодом XAML:  
  
    ```xaml  
    <Grid VerticalAlignment="Top">  
            <StackPanel Orientation="Horizontal">  
                <Border BorderThickness="0,0,1,0" BorderBrush="DarkGray" Margin="0,10" MinWidth="70">  
                    <TextBlock Text="{Binding Number}" FontSize="45" Foreground="DarkGray" Margin="20,0"/>  
                </Border>  
                <StackPanel>  
                    <TextBlock Text="{Binding Title}" Margin="10,10,0,0" FontSize="16" FontWeight="Bold" />  
                    <TextBlock Text="{Binding Description}" Margin="10,0,0,0" TextWrapping="Wrap" MaxWidth="500" />  
                </StackPanel>  
            </StackPanel>  
        </Grid>  
    ```  
  
     Этот код XAML создает повторно используемый шаблон с заполнителями для полей номера, заголовка и описания. Во время выполнения заполнители можно заменять текстом, как показано на рисунке ниже.  
  
     ![Пользовательский элемент управления QuickStartTask](../designers/media/wpfquickstart1.PNG "WPFQuickStart1")  
  
6. В **обозревателе решений**разверните узел **QuickStartTask.xaml** и откройте файл **QuickStartTask.xaml.cs** или **QuickStartTask.xaml.vb** .  
  
7. В редакторе кода замените пространство имен `namespace WPFQuickStart.Common` (C#) или метод `Public Class QuickStartTask` (Visual Basic) следующим кодом:  
  
    ```csharp  
    namespace WPFQuickStart.Common  
    {  
        /// <summary>  
        /// Interaction logic for QuickStartTask.xaml  
        /// </summary>  
        public partial class QuickStartTask : UserControl  
        {  
            public QuickStartTask()  
            {  
                this.InitializeComponent();  
                this.DataContext = this;  
            }  
  
            public int Number  
            {  
                get { return (int)GetValue(NumberProperty); }  
                set { SetValue(NumberProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty NumberProperty =  
                DependencyProperty.Register("Number", typeof(int), typeof(QuickStartTask), new PropertyMetadata(0));  
  
            public string Title  
            {  
                get { return (string)GetValue(TitleProperty); }  
                set { SetValue(TitleProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty TitleProperty =  
                DependencyProperty.Register("Title", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));  
  
            public string Description  
            {  
                get { return (string)GetValue(DescriptionProperty); }  
                set { SetValue(DescriptionProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty DescriptionProperty =  
                DependencyProperty.Register("Description", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));  
        }  
    }  
    ```  
  
    ```vb  
    Partial Public Class QuickStartTask  
            Inherits UserControl  
  
            Public Sub New()  
                Me.InitializeComponent()  
                Me.DataContext = Me  
            End Sub  
  
            Public Property Number() As Integer  
                Get  
                    Return CInt(Fix(GetValue(NumberProperty)))  
                End Get  
                Set(ByVal value As Integer)  
                    SetValue(NumberProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly NumberProperty As DependencyProperty = DependencyProperty.Register("Number", GetType(Integer), GetType(QuickStartTask), New PropertyMetadata(0))  
  
            Public Property Title() As String  
                Get  
                    Return CStr(GetValue(TitleProperty))  
                End Get  
                Set(ByVal value As String)  
                    SetValue(TitleProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly TitleProperty As DependencyProperty = DependencyProperty.Register("Title", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))  
  
            Public Property Description() As String  
                Get  
                    Return CStr(GetValue(DescriptionProperty))  
                End Get  
                Set(ByVal value As String)  
                    SetValue(DescriptionProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly DescriptionProperty As DependencyProperty = DependencyProperty.Register("Description", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))  
        End Class  
    ```  
  
     Этот код использует свойства зависимостей для задания значений полей номера, заголовка и описания во время выполнения.  
  
8. В строке меню выберите **Сборка**&gt; **Собрать WPFQuickStart** , чтобы выполнить сборку пользовательского элемента управления.  
  
#### <a name="to-create-and-modify-the-main-window"></a>Создание и изменение главного окна  
  
1. В **обозревателе решений**откройте файл **MainWindow.xaml** .  
  
2. **Внимание**! Это действие необходимо выполнить только для C#. При использовании Visual Basic перейдите к следующему шагу. В нижней области конструктора найдите строку `xmlns:local=”clr-namespace:WPFQuickStart”` и замените ее следующим кодом XAML:  
  
    ```xaml  
    xmlns:local=”clr-namespace:WPFQuickStart.Common”  
    ```  
  
3. В диалоговом окне **Свойства** разверните узел категории **Common** и выберите свойство **Заголовок** , а затем введите значение `WPF Todo List` и нажмите клавишу **ВВОД** .  
  
     Обратите внимание на то, что элемент **Title** в окне XAML изменится в соответствии с новым значением. Свойства XAML можно изменять как в окне XAML, так и в окне **Свойства** . При этом изменения синхронизируются.  
  
4. В окне XAML задайте для элемента **Height** значение `768`, а для свойства **Width** — значение `1280`.  
  
     Эти элементы соответствуют свойствам **Высота** и **Ширина** в категории **Макет** в окне **Свойства** .  
  
5. Выделите теги `<Grid>` и `</Grid>` и замените их следующим кодом XAML:  
  
    ```xaml  
    <Grid>  
  
            <Grid Margin="50,50,10,10">  
                <Grid.ColumnDefinitions>  
                    <ColumnDefinition Width="*" />  
                    <ColumnDefinition Width="*" />  
                </Grid.ColumnDefinitions>  
                <Grid.RowDefinitions>  
                    <RowDefinition Height="Auto" />  
                    <RowDefinition Height="*" />  
                </Grid.RowDefinitions>  
  
                <Grid Grid.Row="0" Grid.ColumnSpan="2" Margin="0,0,0,20">  
                    <StackPanel>  
                        <TextBlock Foreground="#0094ff" FontFamily="Segoe UI Light" Margin="0,0,0,6">MICROSOFT AZURE MOBILE SERVICES</TextBlock>  
                        <TextBlock Foreground="Gray" FontFamily="Segoe UI Light" FontSize="45" ><Run Text="My Todo List"/></TextBlock>  
                    </StackPanel>  
                </Grid>  
  
                <Grid Grid.Row="1">  
                    <StackPanel>  
  
                        <local:QuickStartTask Number="1" Title="Insert a TodoItem" Description="Enter some text below and click Save to insert a new todo item into the list." />  
  
                        <StackPanel Orientation="Horizontal" Margin="72,0,0,0">  
                            <TextBox x:Name="TodoInput" Margin="5" MinWidth="300"/>  
                            <Button x:Name="ButtonSave" Click="ButtonSave_Click" Content="Save"/>  
                        </StackPanel>  
  
                    </StackPanel>  
                </Grid>  
  
                <Grid Grid.Row="1" Grid.Column="1">  
                    <Grid.RowDefinitions>  
                        <RowDefinition Height="Auto" />  
                        <RowDefinition />  
                    </Grid.RowDefinitions>  
                    <StackPanel>  
                        <local:QuickStartTask Number="2" Title="Query and Update Data" Description="Click the Refresh button to load the unfinished TodoItems from the Azure Mobile Service. Select the checkbox to mark a ToDo item as complete and update the list." />  
                        <Button Margin="72,0,0,0" Name="ButtonRefresh" Click="ButtonRefresh_Click">Refresh</Button>  
                    </StackPanel>  
  
                    <ListView Name="ListItems" Margin="62,10,0,0" Grid.Row="1">  
                        <ListView.ItemTemplate>  
                            <DataTemplate>  
                                <StackPanel Orientation="Horizontal">  
                                    <CheckBox Name="CheckBoxComplete" IsChecked="{Binding Complete, Mode=TwoWay}" Checked="CheckBoxComplete_Checked" Content="{Binding Text}" Margin="10,5" VerticalAlignment="Center"/>  
                                </StackPanel>  
                            </DataTemplate>  
                        </ListView.ItemTemplate>  
                    </ListView>  
  
                </Grid>  
  
            </Grid>  
        </Grid>  
    ```  
  
     Обратите внимание на то, что изменения отражаются в окне конструктора. Как и в предыдущем случае, вы также могли бы определить пользовательский интерфейс, добавив элементы управления из окна **Панель элементов** и задав свойства в окне **Свойства** . Все, что можно сделать в конструкторе, можно сделать и в коде XAML, и наоборот.  
  
     На этом этапе интерфейс должен выглядеть так, как показано на рисунке ниже.  
  
     ![Элемент MainWindow в конструкторе](../designers/media/wpfquickstart2.PNG "WPFQuickStart2")  
  
    > [!NOTE]
    > При выполнении нескольких следующих процедур вы можете увидеть ошибки в **списке ошибок** , если он открыт. Не беспокойтесь, они пропадут после завершения остальных процедур.  
  
6. В **обозревателе решений**разверните узел **MainWindow.xaml** и откройте файл **MainWindow.xaml.cs** или **MainWindow.xaml.vb** .  
  
7. В редакторе кода добавьте в начало файла следующие директивы `using` или `Imports` :  
  
    ```csharp  
    using Microsoft.WindowsAzure.MobileServices;  
    using Newtonsoft.Json;   
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    Imports Newtonsoft.Json  
    ```  
  
8. Замените весь код в пространстве имен **WPFQuickStart** (C#) или классе **Class MainWindow** (Visual Basic) следующим кодом:  
  
    ```csharp  
    namespace WPFQuickStart  
    {  
        /// <summary>  
        /// Interaction logic for MainWindow.xaml  
        /// </summary>  
        public class TodoItem  
        {  
            public string Id { get; set; }  
  
            [JsonProperty(PropertyName = "text")]  
            public string Text { get; set; }  
  
            [JsonProperty(PropertyName = "complete")]  
            public bool Complete { get; set; }  
        }  
  
        public partial class MainWindow : Window  
        {  
            private MobileServiceCollection<TodoItem, TodoItem> items;  
            private IMobileServiceTable<TodoItem> todoTable = App.MobileService.GetTable<TodoItem>();  
  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            private async void InsertTodoItem(TodoItem todoItem)  
            {  
                // This code inserts a new TodoItem into the database. When the operation completes  
                // and Mobile Services has assigned an Id, the item is added to the CollectionView  
                await todoTable.InsertAsync(todoItem);  
                items.Add(todoItem);  
            }  
  
            private async void RefreshTodoItems()  
            {  
                try  
                {  
                    // This code refreshes the entries in the list view by querying the TodoItem table.  
                    // The query excludes completed TodoItems  
                    items = await todoTable  
                        .Where(todoItem => todoItem.Complete == false)  
                        .ToCollectionAsync();  
                    ListItems.ItemsSource = items;  
                }  
                catch (MobileServiceInvalidOperationException e)  
                {  
                    MessageBox.Show(e.Message, "Error loading items");  
                }  
            }  
  
            private async void UpdateCheckedTodoItem(TodoItem item)  
            {  
                // This code takes a freshly completed TodoItem and updates the database. When the MobileService   
                // responds, the item is removed from the list   
                await todoTable.UpdateAsync(item);  
                items.Remove(item);  
            }  
  
            private void ButtonRefresh_Click(object sender, RoutedEventArgs e)  
            {  
                RefreshTodoItems();  
            }  
  
            private void ButtonSave_Click(object sender, RoutedEventArgs e)  
            {  
                var todoItem = new TodoItem { Text = TodoInput.Text };  
                InsertTodoItem(todoItem);  
                TodoInput.Text = "";  
            }  
  
            private void CheckBoxComplete_Checked(object sender, RoutedEventArgs e)  
            {  
                CheckBox cb = (CheckBox)sender;  
                TodoItem item = cb.DataContext as TodoItem;  
                UpdateCheckedTodoItem(item);  
            }  
  
            protected override void OnActivated(EventArgs e)  
            {  
                RefreshTodoItems();  
            }  
        }  
  
    }  
    ```  
  
    ```vb  
    Public Class TodoItem  
        Public Property Id() As String  
  
        <JsonProperty(PropertyName:="text")>  
        Public Property Text() As String  
  
        <JsonProperty(PropertyName:="complete")>  
        Public Property Complete() As Boolean  
    End Class  
  
    Partial Public Class MainWindow  
        Inherits Window  
  
        Private items As MobileServiceCollection(Of TodoItem, TodoItem)  
        Private todoTable As IMobileServiceTable(Of TodoItem) = Application.MobileService.GetTable(Of TodoItem)()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        Private Async Sub InsertTodoItem(ByVal todoItem As TodoItem)  
            ' This code inserts a new TodoItem into the database. When the operation completes  
            ' and Mobile Services has assigned an Id, the item is added to the CollectionView  
            Await todoTable.InsertAsync(todoItem)  
            items.Add(todoItem)  
        End Sub  
  
        Private Async Sub RefreshTodoItems()  
            Dim exception As MobileServiceInvalidOperationException = Nothing  
            Try  
                ' This code refreshes the entries in the list view by querying the TodoItem table.  
                ' The query excludes completed TodoItems  
                items = Await todoTable.Where(Function(todoItem) todoItem.Complete = False).ToCollectionAsync()  
            Catch e As MobileServiceInvalidOperationException  
                exception = e  
            End Try  
  
            If exception IsNot Nothing Then  
                MessageBox.Show(exception.Message, "Error loading items")  
            Else  
                ListItems.ItemsSource = items  
            End If  
        End Sub  
  
        Private Async Sub UpdateCheckedTodoItem(ByVal item As TodoItem)  
            ' This code takes a freshly completed TodoItem and updates the database. When the MobileService   
            ' responds, the item is removed from the list   
            Await todoTable.UpdateAsync(item)  
            items.Remove(item)  
        End Sub  
  
        Private Sub ButtonRefresh_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            RefreshTodoItems()  
        End Sub  
  
        Private Sub ButtonSave_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            Dim todoItem = New TodoItem With {.Text = TodoInput.Text}  
            InsertTodoItem(todoItem)  
            TodoInput.Text = ""  
        End Sub  
  
        Private Sub CheckBoxComplete_Checked(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            Dim cb As CheckBox = DirectCast(sender, CheckBox)  
            Dim item As TodoItem = TryCast(cb.DataContext, TodoItem)  
            UpdateCheckedTodoItem(item)  
        End Sub  
  
        Protected Overrides Sub OnActivated(ByVal e As EventArgs)  
            RefreshTodoItems()  
        End Sub  
    End Class  
    ```  
  
     Этот код определяет взаимодействие между пользовательским интерфейсом и базой данных в мобильной службе с помощью асинхронных методов.  
  
## <a name="create-the-azure-mobile-service"></a>Создание мобильной службы Azure  
 Последний шаг — создание мобильной службы в Microsoft Azure, добавление таблицы для хранения данных и создание ссылки на экземпляр службы в приложении.  
  
#### <a name="to-create-a-mobile-service"></a>Создание мобильной службы  
  
1. Откройте веб-браузер, войдите на портал Microsoft Azure и выберите вкладку **Мобильные службы** .  
  
2. Нажмите кнопку **Создать**, а затем во всплывающем диалоговом окне выберите **СРЕДА ВЫПОЛНЕНИЯ ПРИЛОЖЕНИЙ**, **МОБИЛЬНАЯ СЛУЖБА, СОЗДАТЬ**.  
  
3. В диалоговом окне **Новая мобильная служба** выберите текстовое поле **URL-адрес** и введите `wpfquickstart01`.  
  
    > [!NOTE]
    > Может потребоваться изменить число в URL-адресе. Для каждой мобильной службы в Microsoft Azure требуется уникальный URL-адрес.  
  
     Этот параметр задает URL-адрес для службы `https://wpfquickstart01.azure-mobile.net/`.  
  
4. В списке **База данных** выберите один из вариантов. Так как это приложение, вероятно, будет использоваться не очень интенсивно, можно выбрать вариант **Создать бесплатную базу данных 20 МБ SQL** или бесплатную базу данных, уже связанную с вашей подпиской.  
  
5. В списке **Регион** выберите центр обработки данных, в котором следует развернуть мобильное приложение, а затем нажмите кнопку **Далее** (стрелка вправо).  
  
    > [!NOTE]
    > Для этой службы используется значение параметра **Сервер** по умолчанию ( **JavaScript**).  
  
6. Если вы создаете новую базу данных, на странице **Указать параметры базы данных** в списке **Сервер** выберите пункт **Создать сервер базы данных SQL**, введите **имя входа SQL** и **пароль**, а затем нажмите кнопку **Завершить** (в виде галочки).  
  
7. Если вы выбрали существующую базу данных, на странице **Параметры базы данных** введите **пароль для входа** , а затем нажмите кнопку **Завершить** (в виде галочки).  
  
     Начнется процесс создания мобильной службы. По его завершении состояние изменится на **Готово** , и вы можете переходить к следующему шагу.  
  
8. На портале выберите созданную мобильную службу, а затем нажмите кнопку **Управление ключами** .  
  
9. В диалоговом окне **Управление ключами доступа** скопируйте **ключ приложения**.  
  
     Он будет использоваться в следующей процедуре.  
  
#### <a name="to-create-a-table"></a>Создание таблицы  
  
1. На портале Microsoft Azure нажмите стрелку вправо рядом с именем мобильной службы, в строке меню выберите **Данные**, а затем щелкните ссылку **Добавить таблицу** .  
  
2. В диалоговом окне **Создание новой таблицы** в текстовом поле **Имя таблицы** введите `TodoItem`и нажмите кнопку **Завершить** (в виде галочки).  
  
     Дождитесь, когда таблица будет создана, а затем перейдите к последней процедуре.  
  
#### <a name="to-add-a-declaration-for-the-mobile-service"></a>Добавление объявления для мобильной службы  
  
1. Вернитесь в Visual Studio. В **обозревателе решений**разверните узел **App.xaml** (C#) или **Application.xaml** (Visual Basic) и откройте файл **App.xaml.cs** или **App.xaml.vb** .  
  
2. В редакторе кода добавьте в начало файла следующие директивы `using` или **Imports** :  
  
    ```csharp  
    using Microsoft.WindowsAzure.MobileServices;  
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    ```  
  
3. Добавьте в класс следующее объявление, заменив *YOUR-SERVICE_HERE* URL-адресом вашей службы, а *YOUR-KEY-HERE* — ключом приложения, который вы скопировали в предыдущей процедуре:  
  
    ```csharp  
    public static MobileServiceClient MobileService = new MobileServiceClient(  
                 "https://YOUR-SERVICE-HERE.azure-mobile.net/",  
                 "YOUR-KEY-HERE"  
             );  
    ```  
  
    ```vb  
    Public Shared MobileService As New MobileServiceClient("https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE")  
    ```  
  
     Этот код позволяет приложению получать доступ к мобильной службе, выполняющейся в Microsoft Azure.  
  
## <a name="test-the-application"></a>Тестирование приложения  
 Вот и все! Вы создали классическое приложение WPF, получающее доступ к мобильной службе Azure. Осталось только запустить его и посмотреть, как оно работает.  
  
#### <a name="to-run-the-application"></a>Запуск приложения  
  
1. В строке меню выберите **Отладка**, **Начать отладку** (или нажмите клавишу F5).  
  
2. В диалоговом окне **Insert a TodoItem** (Добавление задачи) введите `Do something`и нажмите кнопку **Save** .  
  
3. ВВОД `Do something else`и нажмите кнопку **Save** .  
  
     Обратите внимание на то, что в списке **Query and Update Data** (Запрос и обновление данных) появились два пункта, как показано на рисунке ниже.  
  
     ![Элементы Todo добавляются в список.](../designers/media/wpfquickstart3.PNG "WPFQuickStart3")  
  
4. Установите флажок **Do something else** в списке.  
  
     Будет вызван метод **UpdateCheckedTodoItem** , и элемент будет удален как из списка, так и из базы данных.  
  
## <a name="next-steps"></a>Следующие шаги  
 Вы ознакомились с весьма простым примером классического приложения WPF, сервером для которого является Azure. Безусловно, реальное приложение скорее всего будет гораздо более сложными, но основные принципы те же. См. статью [WPF в .NET Framework](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx).  
  
 Вы можете сделать пользовательский интерфейс более привлекательным, добавив цвета, фигуры, графические элементы и даже анимацию. См. раздел [Разработка XAML в Visual Studio и Blend для Visual Studio](../designers/designing-xaml-in-visual-studio.md).  
  
 С помощью мобильных служб Azure можно подключаться к существующим базам данных SQL или другим источникам данных. См. [документацию по мобильным службам](https://azure.microsoft.com/services/app-service/mobile/).  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Создание первого классического приложения WPF](../designers/walkthrough-my-first-wpf-desktop-application2.md)   
 [Создание современных приложений для настольных систем с помощью Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
