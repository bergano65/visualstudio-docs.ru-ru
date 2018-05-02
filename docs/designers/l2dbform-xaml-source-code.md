---
title: Исходный код L2DBForm.xaml
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: sample
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70e367342afa442e6e3af83de99c9559baa44892
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="l2dbformxaml-source-code"></a>Исходный код L2DBForm.xaml

Этот раздел содержит и описывает исходный XAML-файл для [WPF Data Binding Using LINQ to XML Example](../designers/wpf-data-binding-using-linq-to-xml-example.md), L2DBForm.xaml.

## <a name="overall-ui-structure"></a>Общая структура интерфейса

Что является типичным для проекта WPF, данный файл содержит один родительский элемент, XML-элемент <xref:System.Windows.Window> , связанный с производным классом `L2XDBFrom` в пространстве имен `LinqToXmlDataBinding` .

Клиентская область располагается в окне <xref:System.Windows.Controls.StackPanel> , имеющем светло-синий фон. Эта панель содержит четыре раздела пользовательского интерфейса <xref:System.Windows.Controls.DockPanel> , разделенные панелями <xref:System.Windows.Controls.Separator> . Назначение этих разделов описывается в подразделе **Примечания** из [предыдущего раздела](../designers/walkthrough-linqtoxmldatabinding-example.md).

Каждый раздел содержит идентифицирующую его метку. В двух первых разделах данная метка повернута на 90 градусов с помощью <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Остальная часть раздела содержит элементы пользовательского интерфейса, соответствующие назначению данного раздела: текстовые поля, блоки текста, кнопки и т. д. Иногда для выравнивания этих дочерних элементов управления используется дочерний элемент <xref:System.Windows.Controls.StackPanel> .

## <a name="window-resource-section"></a>Раздел оконных ресурсов

Открывающий тег `<Window.Resources>` в строке 9 определяет начало раздела оконных ресурсов. Он оканчивается закрывающим тегом в строке 35.

В теге `<ObjectDataProvider>` , который охватывает строки с 11 по 25, объявляется поставщик <xref:System.Windows.Data.ObjectDataProvider>с именем `LoadedBooks`, использующий в качестве источника <xref:System.Xml.Linq.XElement> . Объект <xref:System.Xml.Linq.XElement> инициализируется путем синтаксического анализа XML-документа (элемент `CDATA`). Обратите внимание, что при объявлении и синтаксическом анализе внедренного XML-документа пробелы сохраняются. Это связано с тем, что в элементе управления <xref:System.Windows.Controls.TextBlock>, используемом для отображения необработанного кода XML, не предусмотрены специальные возможности форматирования XML.

Наконец, в строках с 28 по 34 определен шаблон <xref:System.Windows.DataTemplate> под именем `BookTemplate` . Он предназначен для отображения записей в разделе пользовательского интерфейса **Список книг**. В нем используются привязка данных и динамические свойства LINQ to XML для получения идентификатора книги с помощью следующих присваиваний.

```
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a>Код привязки данных

Кроме элемента <xref:System.Windows.DataTemplate> , привязка данных используется во многих других местах данного файла.

В открывающем теге `<StackPanel>` в строке 38 свойство данной панели <xref:System.Windows.FrameworkElement.DataContext%2A> устанавливается на поставщика данных `LoadedBooks` .

```
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

Задание контекста данных позволяет элементу <xref:System.Windows.Controls.TextBlock> с именем `tbRawXml` (в строке 46) отображать необработанный код XML путем привязки к свойству `Xml` этого поставщика данных.

```
Text="{Binding Path=Xml}"
```

Объект <xref:System.Windows.Controls.ListBox> в разделе интерфейса **Список книг** задает в строках с 58 по 62 для своих отображаемых элементов шаблон `BookTemplate` , определенный в разделе ресурсов окна.

```
ItemTemplate ="{StaticResource BookTemplate}"
```

Затем в строках с 59 по 62 действительные значения книг привязываются к данному списку.

```
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

В третьем разделе интерфейса, **Редактировать выбранную книгу**, сначала происходит привязка свойства <xref:System.Windows.FrameworkElement.DataContext%2A> дочернего элемента <xref:System.Windows.Controls.StackPanel> к текущему элементу, выбранному из раздела пользовательского интерфейса **Список книг** (строка 82).

```
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

Затем в нем используется двусторонняя привязка данных, что позволяет отображать и обновлять текущие значения элементов книги с помощью двух текстовых полей данной панели. Привязка данных к динамическим свойствам аналогична используемой в шаблоне данных `BookTemplate`:

```
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

В коде XAML последнего раздела пользовательского интерфейса (**Добавление новой книги**) привязка к данным не используется. Вместо этого привязка данных применяется в коде обработки событий в файле *L2DBForm.xaml.cs*.

## <a name="example"></a>Пример

### <a name="description"></a>Описание:

> [!NOTE]
> Рекомендуется скопировать расположенный ниже код в редактор кода, например редактор исходного кода C# в Visual Studio, чтобы было легче отслеживать номера строк.

### <a name="code"></a>Код

```xml
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:system="clr-namespace:System;assembly=mscorlib"
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"
    xmlns:local="clr-namespace:LinqToXmlDataBinding"
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">

    <Window.Resources>
        <!-- Books provider and inline data -->
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">
            <ObjectDataProvider.MethodParameters>
                <system:String xml:space="preserve">
<![CDATA[
<books xmlns="http://www.mybooks.com">
  <book id="0">book zero</book>
  <book id="1">book one</book>
  <book id="2">book two</book>
  <book id="3">book three</book>
</books>
]]>
                </system:String>
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>
            </ObjectDataProvider.MethodParameters>
        </ObjectDataProvider>

        <!-- Template for use in Books List listbox. -->
        <DataTemplate x:Key="BookTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>
                <TextBlock Margin="3" Text="-"/>
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

    <!-- Main visual content container -->
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">
        <!-- Raw XML display section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML
            <Label.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Label.LayoutTransform>
            </Label>
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- List box to display all books section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List
                <Label.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Label.LayoutTransform>
            </Label>
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">
                <ListBox.ItemsSource>
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
                </ListBox.ItemsSource>
            </ListBox>
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">
            <Button.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Button.LayoutTransform>
            </Button>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Edit current selection section -->
        <DockPanel Margin="5">
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">
                    Changes are live!
                <TextBlock.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </TextBlock.LayoutTransform>
            </TextBlock>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book ID and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book Value and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Add new book section -->
        <DockPanel Margin="5">
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book
                <Button.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Button.LayoutTransform>
            </Button>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>
                <StackPanel Margin="1">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="tbAddID" Width="410">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="tbAddValue" Width="410" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>
    </StackPanel>
</Window>

```

### <a name="comments"></a>Комментарии

Сведения об исходном коде для обработчиков событий, связанных с элементами интерфейса WPF, см. в разделе [L2DBForm.xaml.cs Source Code](../designers/l2dbform-xaml-cs-source-code.md).

## <a name="see-also"></a>См. также

- [Пошаговое руководство. Пример LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Исходный код L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)