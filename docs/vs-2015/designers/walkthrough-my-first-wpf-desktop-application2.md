---
title: Пошаговое руководство. Создание первого классического приложения WPF 2 | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3c460fa9-2ea1-413f-ae54-54a1f2a499d1
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e800fe651d32435351b2338b4da2f9c55158b3a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663994"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Пошаговое руководство. Создание первого классического приложения WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

a Name = "Введение" >в </a> этом пошаговом руководстве приводятся общие сведения о разработке Windows Presentation Foundation (WPF). Вы создадите простейшее приложение, содержащее элементы, используемые в большинстве классических приложений WPF: разметку XAML, код программной части, определения приложения, элементы управления, макет, привязку данных и стили.

## <a name="creating-the-application-project"></a><a name="Create_The_Application_Code_Files"></a> Создание проекта приложения
 В этом разделе вы создадите инфраструктуру приложения, включающую в себя проект и главное окно или форму.

#### <a name="to-create-the-project"></a>Создание проекта

1. В строке меню выберите **Файл**, **Создать**, **Проект**.

2. В диалоговом окне **Новый проект** разверните узел **Visual C#** или **Visual Basic** и выберите узел **Окна** , а затем разверните узел **Окна** и выберите узел **Классический рабочий стол** .

3. В списке шаблонов выберите шаблон **Приложение WPF** .

4. В диалоговом окне **Имя** введите `ExpenseIt`и нажмите кнопку **ОК** .

     Будет создан проект, файлы проекта добавятся в **обозреватель решений**, и откроется конструктор окна приложения по умолчанию с именем **MainWindow.xaml** .

#### <a name="to-modify-the-main-window"></a>Изменение главного окна

1. В конструкторе перейдите на вкладку **MainWindow.xaml** , если она еще не является активной вкладкой конструктора.

2. Если вы используете C#, найдите строку `<Window x:Class="ExpenseIt.MainWindow"` и замените ее строкой `<NavigationWindow x:Class="ExpenseIt.MainWindow"`.

     Если вы используете Visual Basic, найдите строку `<Window x:Class=" MainWindow"` и замените ее строкой `<NavigationWindow x:Class="MainWindow"`.

     Обратите внимание на то, что при замене тега `<Window` на `<NavigationWindow`Intellisense автоматически также заменяет закрывающий тег на `</NavigationWindow>` .

    > [!NOTE]
    > Если после замены тега окно **Список ошибок** открыто, вы можете заметить несколько ошибок. Не беспокойтесь: после внесения изменений в следующих шагах они исчезнут.

3. Выберите теги `<Grid>` и `</Grid>` и удалите их.

     **NavigationWindow** не может содержать другие элементы пользовательского интерфейса, например **Grid**.

4. В диалоговом окне **Свойства** разверните узел категории **Common** и выберите свойство **Заголовок** , а затем введите значение `ExpenseIt` и нажмите клавишу **ВВОД** .

     Обратите внимание на то, что элемент **Title** в окне XAML изменится в соответствии с новым значением. Свойства XAML можно изменять как в окне XAML, так и в окне **Свойства** . При этом изменения синхронизируются.

5. В окне XAML задайте для элемента **Height** значение `375`, а для свойства **Width** — значение `500`.

     Эти элементы соответствуют свойствам **Высота** и **Ширина** в категории **Макет** в окне **Свойства** .

     Файл **MainWindow.xaml** на C# теперь должен выглядеть так:

    ```xaml
    <NavigationWindow x:Class="ExpenseIt.MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500">

    </NavigationWindow>
    ```

     Или так на Visual Basic:

    ```xaml
    <NavigationWindow x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500">

    </NavigationWindow>
    ```

#### <a name="to-modify-the-code-behind-file-c"></a>Изменение файла с кодом программной части (C#)

1. В **обозревателе решений**разверните узел **MainWindow.xaml** и откройте файл **MainWindow.xaml.cs** .

2. Найдите строку `public partial class MainWindow : Window` и замените ее на `public partial class MainWindow : NavigationWindow`.

     Это приведет к тому, что класс `MainWindow` будет наследоваться от `NavigationWindow`. В Visual Basic это происходит автоматически при изменении окна в XAML, поэтому изменять код не нужно.

## <a name="adding-files-to-the-application"></a><a name="add_files_to_the_application"></a> Добавление файлов в приложение
 В этом разделе вы добавите в приложение две страницы и изображение.

#### <a name="to-add-a-home-screen"></a>Добавление начального экрана

1. В **обозревателе решений**откройте контекстное меню узла **ExpenseIt** и выберите команду **Добавить**, **Страница**.

2. В диалоговом окне **Добавление нового элемента** выберите текстовое поле **Имя** и введите значение `ExpenseItHome`, а затем нажмите кнопку **Добавить** .

     Эта страница представляет собой первое окно, которое будет открываться при запуске приложения.

3. В конструкторе перейдите на вкладку **ExpenseItHome.xaml** , если она еще не является активной вкладкой конструктора.

4. Выберите элемент `<Title>` и измените заголовок на **ExpenseIt — домашняя страница**.

     Файл **ExpenseItHome.xaml** на C# теперь должен выглядеть так:

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home">

        <Grid>

        </Grid>
    </Page>
    ```

     Или так на Visual Basic:

    ```xaml
    <Page x:Class="ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home">
        <Grid>

        </Grid>
    </Page>
    ```

5. В конструкторе откройте вкладку **MainWindow.xaml** .

6. Найдите элемент `Title="ExpenseIt" Height="375" Width="500">` строки и добавьте свойство `Source="ExpenseItHome.xaml"` .

     Это задает **ExpenseItHome. XAML** в качестве первой страницы, открытой при запуске приложения. Файл **MainWindow.xaml** на C# теперь должен выглядеть так:

    ```xaml
    <NavigationWindow x:Class="ExpenseIt.MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">

    </NavigationWindow>
    ```

     Или так на Visual Basic:

    ```xaml
    <NavigationWindow x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">

    </NavigationWindow>
    ```

     Так же как и в случае с ранее заданными свойствами, вы могли задать свойство `Source` в категории **Прочие** в окне **Свойства** .

#### <a name="to-add-a-details-window"></a>Добавление окна сведений

1. В **обозревателе решений**откройте контекстное меню узла **ExpenseIt** и выберите команду **Добавить**, **Страница**.

2. В диалоговом окне **Добавление нового элемента** выберите текстовое поле **Имя** и введите значение `ExpenseReportPage`, а затем нажмите кнопку **Добавить** .

     В этом окне будет выводиться отдельный отчет по расходам.

3. В конструкторе перейдите на вкладку **ExpenseReportPage.xaml** , если она еще не является активной вкладкой конструктора.

4. Выберите элемент `<Title>` и измените заголовок на **ExpenseIt — просмотр расходов**.

     Файл ExpenseReportPage.xaml на C# теперь должен выглядеть так:

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseReportPage"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - View Expense">

        <Grid>

        </Grid>
    </Page>
    ```

     Или так на Visual Basic:

    ```xaml
    <Page x:Class="ExpenseReportPage"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - View Expense">
        <Grid>

        </Grid>
    </Page>
    ```

5. Чтобы запустить приложение, в меню **Отладка**выберите команду **Начать отладку** (или нажмите клавишу F5).

     На рисунке ниже показано приложение с кнопками навигации по окну.

     ![Снимок экрана примера ExpenseIt](../designers/media/gettingstartedfigure1.png "GettingStartedFigure1")

6. Закройте приложение, чтобы вернуться в режим конструктора.

## <a name="creating-the-user-interface"></a><a name="Add_Layout"></a> Создание пользовательского интерфейса
 Макет позволяет упорядочивать размещение элементов, а также управлять их размером и положением при изменении размеров формы. В этом разделе вы создадите сетку с одним столбцом и тремя строками. Вы добавите элементы управления на две страницы, добавите код и, наконец, определите повторно используемые стили для элементов управления.

#### <a name="to-create-the-layout"></a>Создание макета

1. Откройте **ExpenseItHome. XAML** и выберите `<Grid>` элемент.

2. В диалоговом окне **Свойства** разверните узел категории **Макет** и задайте для свойств **Поле** значения `10`, `10`, `0`и `10`, которые соответствуют левому, правому, верхнему и нижнему полям.

     Элемент `Margin="10,0,10,10"` будет добавлен в элемент `<Grid>` в коде XAML. Эти значения можно было бы также ввести непосредственно в коде XAML, а не в окне **Свойства** , — результат был бы тем же.

3. Добавьте следующий код XAML в элемент `Grid` , чтобы создать определения строк и столбцов:

    ```xaml
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition />
        <RowDefinition Height="Auto"/>
    </Grid.RowDefinitions>
    ```

#### <a name="to-add-controls"></a>Добавление элементов управления

1. Откройте файл **ExpenseItHome.xaml**.

2. Добавьте приведенный ниже код XAML непосредственно над тегом `</Grid>` , чтобы создать элементы управления `Border`, `ListBox` и `Button` .

    ```xaml
    <!-- People list -->
      <Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">
          <Label VerticalAlignment="Center" Foreground="White">Names</Label>
      </Border>
      <ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1">
          <ListBoxItem>Mike</ListBoxItem>
          <ListBoxItem>Lisa</ListBoxItem>
          <ListBoxItem>John</ListBoxItem>
          <ListBoxItem>Mary</ListBoxItem>
      </ListBox>

      <!-- View report button -->
      <Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>

    ```

     Обратите внимание на то, что элементы управления появятся в окне разработки. Элементы управления можно было бы также создать, перетащив их из окна **Панель элементов** в окно разработки и задав их свойства в окне **Свойства** .

3. Выполните сборку и запустите приложение. На рисунке ниже показано, как выглядят элементы управления, созданные с помощью кода XAML в этой процедуре, во время выполнения.

     ![Снимок экрана примера ExpenseIt](../designers/media/gettingstartedfigure2.png "GettingStartedFigure2")

4. Закройте приложение, чтобы вернуться в режим конструктора.

#### <a name="to-add-a-background-image"></a>Добавление фонового изображения

1. Выберите приведенное ниже изображение и сохраните его с именем `watermark.png`.

     ![Изображение водяного знака для пошагового руководства](../designers/media/wpf-watermark.png "WPF_watermark")

    > [!NOTE]
    > Вы также можете создать собственное изображение и сохранить его с именем `watermark.png`.

2. В **обозревателе решений**откройте контекстное меню узла **ExpenseIt** и выберите команду **Добавить**, **Существующий элемент**.

3. В диалоговом окне **Добавление существующего элемента** найдите только что добавленное изображение **watermark.png** , выберите его, а затем нажмите кнопку **Добавить** .

    > [!NOTE]
    > Может потребоваться развернуть список **Типы файлов** и выбрать пункт **Файлы изображений**.

4. Откройте файл **ExpenseItHome.xaml** и добавьте следующий код XAML непосредственно над тегом `</Grid>` , чтобы создать фоновое изображение:

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png"/>
    </Grid.Background>

    ```

#### <a name="to-add-a-title"></a>Добавление заголовка

1. Откройте файл **ExpenseItHome.xaml**.

2. Найдите строку `<Grid.ColumnDefinitions>` и добавьте следующий код сразу под ней:

    ```xaml
    <ColumnDefinition Width="230" />

    ```

     Слева от существующих столбцов будет создан дополнительный столбец фиксированной ширины в 230 пикселей.

3. Найдите строку `<Grid.RowDefinitions>` и добавьте следующий код сразу под ней:

    ```xaml
    <RowDefinition />

    ```

     В начало сетки будет добавлена строка.

4. Переместите элементы управления во второй столбец, присвоив `Grid.Column` значение 1. Переместите каждый элемент управления на одну строку вниз, увеличив значение каждого свойства `Grid.Row` на 1.

    1. Найдите строку `<Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">`. Измените `Grid.Column="0"` на `Grid.Column="1"` , а `Grid.Row="0"` — на `Grid.Row="1"`.

    2. Найдите строку `<ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"`. Измените `Grid.Column="0"` на `Grid.Column="1"` , а `Grid.Row="1"` — на `Grid.Row="2"`.

    3. Найдите строку `<Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"`. Измените `Grid.Column="0"` на `Grid.Column="1"` , а `Grid.Row="2"` — на `Grid.Row="3"`.

5. Непосредственно перед элементом `<Border` добавьте следующий код XAML для вывода заголовка:

    ```xaml
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
        View Expense Report
    </Label>

    ```

     Содержимое файла **ExpenseItHome.xaml** на C# теперь должно выглядеть так:

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home">
        <Grid Margin="10,0,10,10">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="230" />
                <ColumnDefinition />
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>
            </Border>
            <!-- People list -->
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
                View Expense Report
            </Label>
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">
                <ListBoxItem>Mike</ListBoxItem>
                <ListBoxItem>Lisa</ListBoxItem>
                <ListBoxItem>John</ListBoxItem>
                <ListBoxItem>Mary</ListBoxItem>
            </ListBox>

            <!-- View report button -->
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>
            <Grid.Background>
                <ImageBrush ImageSource="watermark.png"/>
            </Grid.Background>
        </Grid>
    </Page>
    ```

     Или так на Visual Basic:

    ```xaml
    <Page x:Class="ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home" >
        <Grid Margin="10,0,10,10">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="230" />
                <ColumnDefinition />
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>
            </Border>
            <!-- People list -->
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
                View Expense Report
            </Label>
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">
                <ListBoxItem>Mike</ListBoxItem>
                <ListBoxItem>Lisa</ListBoxItem>
                <ListBoxItem>John</ListBoxItem>
                <ListBoxItem>Mary</ListBoxItem>
            </ListBox>

            <!-- View report button -->
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>
            <Grid.Background>
                <ImageBrush ImageSource="watermark.png"/>
            </Grid.Background>
        </Grid>
    </Page>
    ```

6. Если сейчас выполнить сборку и запуск приложения, оно должно выглядеть, как показано на рисунке ниже.

     ![Снимок экрана примера ExpenseIt](../designers/media/gettingstartedfigure3.png "GettingStartedFigure3")

#### <a name="to-add-code-to-the-button"></a>Добавление кода в кнопку

1. Откройте файл **ExpenseItHome.xaml**.

2. Выберите элемент `<Button` и добавьте следующий код XAML сразу же после элемента **HorizontalAlignment="Right"** : `Click="Button_Click"`.

     Будет добавлен обработчик событий `Click` кнопки. Теперь код элемента ** кнопки<** должен выглядеть следующим образом:

    ```
    <!-- View report button -->
      <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right" Click="Button_Click">View</Button>
    ```

3. Откройте файл **ExpenseItHome.xaml.cs** или **ExpenseItHome.xaml.vb** .

4. Добавьте следующий код в класс `ExpenseItHome` :

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        // View Expense Report
        ExpenseReportPage expenseReportPage = new ExpenseReportPage();
        this.NavigationService.Navigate(expenseReportPage);

    }
    ```

    ```vb
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
        ' View Expense Report
        Dim expenseReportPage As New ExpenseReportPage()
    Me.NavigationService.Navigate(expenseReportPage)
    End Sub
    ```

     Этот обработчик событий открывает страницу отчета по расходам при нажатии кнопки.

#### <a name="to-create-the-ui-for-the-report-page"></a>Создание пользовательского интерфейса для страницы отчета

1. Откройте **файл ExpenseReportPage. XAML**.

     На этой странице будет выводиться отчет по расходам для человека, выбранного на домашней странице.

2. Добавьте следующий код XAML между тегами `<Grid>` и `</Grid>` :

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png" />
    </Grid.Background>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="230" />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto" />
        <RowDefinition />
    </Grid.RowDefinitions>

    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
    FontWeight="Bold" FontSize="18" Foreground="#0066cc">
        Expense Report For:
    </Label>
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">

        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="Auto" />
            <RowDefinition />
        </Grid.RowDefinitions>

        <!-- Name -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
            <Label Margin="0,0,0,5" FontWeight="Bold">Name:</Label>
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>
        </StackPanel>

        <!-- Department -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">
            <Label Margin="0,0,0,5" FontWeight="Bold">Department:</Label>
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>
        </StackPanel>

        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"
              HorizontalAlignment="Left">
            <!-- Expense type and Amount table -->
            <DataGrid  AutoGenerateColumns="False" RowHeaderWidth="0" >
                <DataGrid.ColumnHeaderStyle>
                    <Style TargetType="{x:Type DataGridColumnHeader}">
                        <Setter Property="Height" Value="35" />
                        <Setter Property="Padding" Value="5" />
                        <Setter Property="Background" Value="#4E87D4" />
                        <Setter Property="Foreground" Value="White" />
                    </Style>
                </DataGrid.ColumnHeaderStyle>
                <DataGrid.Columns>
                    <DataGridTextColumn Header="ExpenseType" />
                    <DataGridTextColumn Header="Amount"  />
                </DataGrid.Columns>
            </DataGrid>
        </Grid>
    </Grid>
    ```

     Этот пользовательский интерфейс похож на созданный для домашней страницы, но данные отчета выводятся в элементе управления **DataGrid** .

3. Выполните сборку и запустите приложение.

4. Нажмите кнопку **Просмотр** .

     Появится страница отчета по расходам.

     На рисунке ниже показана страница отчета по расходам. Обратите внимание на то, что кнопка возврата активна.

     ![Снимок экрана примера ExpenseIt](../designers/media/gettingstartedfigure4.png "GettingStartedFigure4")

#### <a name="to-style-controls"></a>Определение стиля элементов управления

1. Откройте файл **App.xaml** (C#) или **Application.xaml** (Visual Basic).

2. Добавьте следующий код XAML между тегами `<Application.Resources>` и `</Application.Resources>` :

    ```xaml
    <!-- Header text style -->
    <Style x:Key="headerTextStyle">
        <Setter Property="Label.VerticalAlignment" Value="Center"></Setter>
        <Setter Property="Label.FontFamily" Value="Trebuchet MS"></Setter>
        <Setter Property="Label.FontWeight" Value="Bold"></Setter>
        <Setter Property="Label.FontSize" Value="18"></Setter>
        <Setter Property="Label.Foreground" Value="#0066cc"></Setter>
    </Style>

    <!-- Label style -->
    <Style x:Key="labelStyle" TargetType="{x:Type Label}">
        <Setter Property="VerticalAlignment" Value="Top" />
        <Setter Property="HorizontalAlignment" Value="Left" />
        <Setter Property="FontWeight" Value="Bold" />
        <Setter Property="Margin" Value="0,0,0,5" />
    </Style>

    <!-- DataGrid header style -->
    <Style x:Key="columnHeaderStyle" TargetType="{x:Type DataGridColumnHeader}">
        <Setter Property="Height" Value="35" />
        <Setter Property="Padding" Value="5" />
        <Setter Property="Background" Value="#4E87D4" />
        <Setter Property="Foreground" Value="White" />
    </Style>

    <!-- List header style -->
    <Style x:Key="listHeaderStyle" TargetType="{x:Type Border}">
        <Setter Property="Height" Value="35" />
        <Setter Property="Padding" Value="5" />
        <Setter Property="Background" Value="#4E87D4" />
    </Style>

    <!-- List header text style -->
    <Style x:Key="listHeaderTextStyle" TargetType="{x:Type Label}">
        <Setter Property="Foreground" Value="White" />
        <Setter Property="VerticalAlignment" Value="Center" />
        <Setter Property="HorizontalAlignment" Value="Left" />
    </Style>

    <!-- Button style -->
    <Style x:Key="buttonStyle" TargetType="{x:Type Button}">
        <Setter Property="Width" Value="125" />
        <Setter Property="Height" Value="25" />
        <Setter Property="Margin" Value="0,10,0,0" />
        <Setter Property="HorizontalAlignment" Value="Right" />
    </Style>
    ```

     Этот код XAML добавляет следующие стили:

    - `headerTextStyle`для форматирования заголовка страницы `Label`;

    - `labelStyle`для форматирования элементов управления `Label` ;

    - `columnHeaderStyle`для форматирования `DataGridColumnHeader`;

    - `listHeaderStyle`для форматирования элементов управления `Border` заголовков списка;

    - `listHeaderTextStyle`— Форматирование **метки**заголовка списка.

    - `buttonStyle`: Для форматирования в `Button` **ExpenseItHome. XAML** форматирования элемента управления.

3. Откройте **ExpenseItHome. XAML** и замените все элементы между `<Grid>` `</Grid>` элементами и следующим кодом XAML.

    ```xaml
    <Grid.ColumnDefinitions>
                <ColumnDefinition Width="230" />
                <ColumnDefinition />
            </Grid.ColumnDefinitions>

            <Grid.RowDefinitions>
                <RowDefinition/>
                <RowDefinition Height="Auto"/>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <Label Grid.Column="1" Style="{StaticResource headerTextStyle}" >
                View Expense Report
            </Label>
            <!-- People list -->
                  <Border Grid.Column="1" Grid.Row="1" Style="{StaticResource listHeaderStyle}">
                <Label Style="{StaticResource listHeaderTextStyle}">Names</Label>
            </Border>
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">
                <ListBoxItem>Mike</ListBoxItem>
                <ListBoxItem>Lisa</ListBoxItem>
                <ListBoxItem>John</ListBoxItem>
                <ListBoxItem>Mary</ListBoxItem>
            </ListBox>

            <!-- View report button -->
            <Button Grid.Column="1" Grid.Row="3" Click="Button_Click" Style="{StaticResource buttonStyle}">View</Button>
            <Grid.Background>
                <ImageBrush ImageSource="watermark.png"  />
            </Grid.Background>
    ```

     Свойства, определяющие внешний вид элементов управления, такие как `VerticalAlignment` и `FontFamily` , при применении стилей удаляются и заменяются.

4. Откройте **файл ExpenseReportPage. XAML** и замените все между `<Grid>` последними `</Grid>` элементами и следующим кодом XAML.

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png" />
    </Grid.Background>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="230" />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto" />
        <RowDefinition />
    </Grid.RowDefinitions>
    <Label Grid.Column="1" Style="{StaticResource headerTextStyle}">
        Expense Report For:
    </Label>
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="Auto" />
            <RowDefinition />
        </Grid.RowDefinitions>

        <!-- Name -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
            <Label Style="{StaticResource labelStyle}">Name:</Label>
            <Label Style="{StaticResource labelStyle}"></Label>
        </StackPanel>

        <!-- Department -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1"
    Orientation="Horizontal">
            <Label Style="{StaticResource labelStyle}">Department:</Label>
            <Label Style="{StaticResource labelStyle}"></Label>
        </StackPanel>

        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"
              HorizontalAlignment="Left">
            <!-- Expense type and Amount table -->
            <DataGrid ColumnHeaderStyle="{StaticResource columnHeaderStyle}"
                      AutoGenerateColumns="False" RowHeaderWidth="0" >
                <DataGrid.Columns>
                    <DataGridTextColumn Header="ExpenseType" />
                    <DataGridTextColumn Header="Amount"  />
                </DataGrid.Columns>
            </DataGrid>
        </Grid>
    </Grid>

    ```

     В элементы `<Label>` и `<Border>` будут добавлены стили.

## <a name="connecting-to-data"></a>Подключение к данным
 В этом разделе вы создадите поставщик данных и шаблон данных, а затем подключите элементы управления для вывода данных.

#### <a name="to-bind-data-to-a-control"></a>Привязка данных к элементу управления

1. Откройте файл **ExpenseItHome.xaml** и выберите элемент `<Grid>` .

2. Добавьте следующий код XAML:

    ```xaml

    <Grid.Resources>
    <!-- Expense Report Data -->
    <XmlDataProvider x:Key="ExpenseDataSource" XPath="Expenses">
        <x:XData>
            <Expenses xmlns="">
                <Person Name="Mike" Department="Legal">
                    <Expense ExpenseType="Lunch" ExpenseAmount="50" />
                    <Expense ExpenseType="Transportation" ExpenseAmount="50" />
                </Person>
                <Person Name="Lisa" Department="Marketing">
                    <Expense ExpenseType="Document printing"
          ExpenseAmount="50"/>
                    <Expense ExpenseType="Gift" ExpenseAmount="125" />
                </Person>
                <Person Name="John" Department="Engineering">
                    <Expense ExpenseType="Magazine subscription"
         ExpenseAmount="50"/>
                    <Expense ExpenseType="New machine" ExpenseAmount="600" />
                    <Expense ExpenseType="Software" ExpenseAmount="500" />
                </Person>
                <Person Name="Mary" Department="Finance">
                    <Expense ExpenseType="Dinner" ExpenseAmount="100" />
                </Person>
            </Expenses>
        </x:XData>
    </XmlDataProvider>
    </Grid.Resources>
    ```

     Этот код создает класс `XmlDataProvider` , который содержит данные для каждого человека. Обычно такие данные загружаются в виде файла, но для простоты в этом примере они добавляются в коде.

3. Внутри элемента `<Grid.Resources>` добавьте следующий код XAML:

    ```xaml
    <!-- Name item template -->
    <DataTemplate x:Key="nameItemTemplate">
        <Label Content="{Binding XPath=@Name}"/>
    </DataTemplate>
    ```

     Будет добавлен `Data Template` , который определяет способ вывода данных в элементе управления **ListBox**.

4. Замените существующий элемент `<ListBox>` следующим кодом XAML:

    ```xaml
    <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"
             ItemsSource="{Binding Source={StaticResource ExpenseDataSource}, XPath=Person}"
             ItemTemplate="{StaticResource nameItemTemplate}">
    </ListBox>
    ```

     Этот код привязывает свойство `ItemsSource` элемента управления `ListBox` к источнику данных, а затем применяет шаблон данных как `ItemTemplate`.

#### <a name="to-connect-data-to-controls"></a>Подключение данных к элементам управления

1. Откройте файл **ExpenseReportPage.xaml.vb** или **ExpenseReportPage.xaml.cs**.

2. Если вы используете C#, добавьте в класс **ExpenseReportPage** приведенный ниже конструктор. Если вы используете Visual Basic, замените существующий класс на следующий:

    ```csharp
    // Custom constructor to pass expense report data
        public ExpenseReportPage(object data):this()
        {
            // Bind to expense report data.
            this.DataContext = data;
        }
    ```

    ```vb
    Partial Public Class ExpenseReportPage
    Inherits Page
    Public Sub New()
    InitializeComponent()
    End Sub

    ' Custom constructor to pass expense report data
    Public Sub New(ByVal data As Object)
    Me.New()
    ' Bind to expense report data.
    Me.DataContext = data
    End Sub

    End Class
    ```

     Этот конструктор принимает объект данных в качестве параметра. В этом случае объект данных будет содержать имя выбранного человека.

3. Откройте файл **ExpenseItHome.xaml.vb** или **ExpenseItHome.xaml.cs**.

4. Замените код обработчика событий `Click` следующим кодом:

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        // View Expense Report
        ExpenseReportPage expenseReportPage = new ExpenseReportPage(this.peopleListBox.SelectedItem);
        this.NavigationService.Navigate(expenseReportPage);

    }
    ```

    ```vb
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
        ' View Expense Report
        Dim expenseReportPage As New ExpenseReportPage(Me.peopleListBox.SelectedItem)
        Me.NavigationService.Navigate(expenseReportPage)
    End Sub
    ```

     Этот код вызывает новый конструктор.

#### <a name="to-update-the-ui-with-data-templates"></a>Обновление пользовательского интерфейса с помощью шаблонов данных

1. Откройте **файл ExpenseReportPage. XAML**.

2. Замените код XAML элементов **Имя** и **и**`<StackPanel` следующим кодом:

    ```xaml
    <!-- Name -->
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
        <Label Style="{StaticResource labelStyle}">Name:</Label>
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Name}"></Label>
    </StackPanel>

    <!-- Department -->
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">
        <Label Style="{StaticResource labelStyle}">Department:</Label>
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Department}"></Label>
    </StackPanel>

    ```

     Этот код привязывает элементы управления **Label** к соответствующим свойствам источника данных.

3. Внутри элемента `<Grid>` добавьте следующий код XAML:

    ```xaml
    <!--Templates to display expense report data-->
    <Grid.Resources>
        <!-- Reason item template -->
        <DataTemplate x:Key="typeItemTemplate">
            <Label Content="{Binding XPath=@ExpenseType}"/>
        </DataTemplate>
        <!-- Amount item template -->
        <DataTemplate x:Key="amountItemTemplate">
            <Label Content="{Binding XPath=@ExpenseAmount}"/>
        </DataTemplate>
    </Grid.Resources>

    ```

     Он определяет способ вывода данных отчета по расходам.

4. Замените элемент `<DataGrid>` следующим кодом:

    ```xaml
    <!-- Expense type and Amount table -->
    <DataGrid ItemsSource="{Binding XPath=Expense}" ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" >

        <DataGrid.Columns>
            <DataGridTextColumn Header="ExpenseType" Binding="{Binding XPath=@ExpenseType}"  />
            <DataGridTextColumn Header="Amount" Binding="{Binding XPath=@ExpenseAmount}" />
        </DataGrid.Columns>

    </DataGrid>
    ```

     Этот код добавляет объект **ItemSource** и определяет привязки для элементов расходов.

5. Выполните сборку и запустите приложение.

6. Выберите человека и нажмите кнопку **Просмотр** .

     На рисунке ниже показаны обе страницы приложения ExpenseIt с элементами управления, макетом, стилями, привязкой данных и примененными шаблонами данных.

     ![Снимки экрана примера ExpenseIt](../designers/media/gettingstartedfigure5.png "GettingStartedFigure5")

## <a name="best-practices"></a><a name="Best_Practices"></a> Рекомендации
 В этом примере продемонстрированы основные принципы разработки на основе WPF, поэтому в нем не соблюдаются рекомендации по разработке приложений. Полное описание рекомендаций по разработке приложений с помощью WPF и .NET Framework см. в следующих разделах:

- Специальные возможности — рекомендации по [специальным возможностям](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx)

- Безопасность: [Безопасность платформы Windows Presentation Foundation](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)

- Локализация: [Общие сведения о глобализации и локализации WPF](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)

- Производительность [Улучшение производительности приложений WPF](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)

## <a name="whats-next"></a><a name="Whats_Next"></a> Что дальше
 Вы освоили ряд приемов создания классических приложений с помощью WPF. У вас должно было сложиться общее представление о составных элементах приложения WPF, привязанного к данным. Информация в этом разделе ни в коем случае не является исчерпывающей, но мы надеемся, что у вас также есть теперь некоторое представление о возможностях, которые вы можете изучить самостоятельно, помимо рассмотренных в этом разделе.

 Более подробную информацию об архитектуре и моделях программирования WPF см. в следующих разделах:

- [Архитектура WPF](https://msdn.microsoft.com/library/ms750441\(v=vs.100\).aspx)

- [Общие сведения о XAML](https://msdn.microsoft.com/library/ms752059\(v=vs.100\).aspx)

- [Общие сведения о свойствах зависимости](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx)

- [Система макета](https://msdn.microsoft.com/library/ms745058\(v=vs.100\).aspx)

- [Стили и шаблоны](https://msdn.microsoft.com/library/bb613570\(v=vs.100\).aspx)

  Более подробную информацию о создании приложений см. в следующих разделах:

- [Обзор разработки приложений](https://msdn.microsoft.com/library/bb613549\(v=vs.100\).aspx)

- [Обзор элементов управления](https://msdn.microsoft.com/library/bb613551\(v=vs.100\).aspx)

- [Общие сведения о привязке данных](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx)

- [Общие сведения о графике, анимации и мультимедиа в WPF](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx)

- [Документы в WPF](https://msdn.microsoft.com/library/ms748388\(v=vs.100\).aspx)

## <a name="see-also"></a>См. также:
 [Пошаговое руководство. Создание классического приложения WPF, подключенного к мобильной службе Azure](../designers/walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service.md) [, создание современных классических приложений с помощью Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
