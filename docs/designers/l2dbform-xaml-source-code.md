---
title: "Исходный код L2DBForm.xaml | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
caps.latest.revision: 2
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b62eac5ab4b057e26ed4a0a34551655984449cf1
ms.lasthandoff: 02/22/2017

---
# <a name="l2dbformxaml-source-code"></a>Исходный код L2DBForm.xaml
Этот раздел содержит исходный код и описание XAML-файла L2DBForm.xaml для [привязки данных WPF с использованием примера LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md).  
  
## <a name="overall-ui-structure"></a>Общая структура интерфейса  
 Как любой типичный проекта WPF, этот файл содержит один родительский XML-элемент <xref:System.Windows.Window>, связанный с производным классом `L2XDBFrom` в пространстве имен `LinqToXmlDataBinding`.  
  
 Клиентская область располагается в окне <xref:System.Windows.Controls.StackPanel> с голубым фоном. Эта панель содержит четыре раздела <xref:System.Windows.Controls.DockPanel>, разделенных полосами <xref:System.Windows.Controls.Separator>. Назначение этих разделов описывается в подразделе **Примечания** в [предыдущем разделе](../designers/walkthrough-linqtoxmldatabinding-example.md).  
  
 Каждый раздел содержит идентифицирующую его метку. В двух первых разделах эта метка повернута на 90 градусов с помощью <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Остальная часть раздела содержит элементы пользовательского интерфейса, соответствующие назначению данного раздела: текстовые поля, блоки текста, кнопки и т. д. Иногда для выравнивания этих дочерних элементов управления используется дочерний элемент <xref:System.Windows.Controls.StackPanel>.  
  
## <a name="window-resource-section"></a>Раздел оконных ресурсов  
 Открывающий тег `<Window.Resources>` в строке 9 определяет начало раздела оконных ресурсов. Он оканчивается закрывающим тегом в строке 35.  
  
 Тег `<ObjectDataProvider>`, который охватывает строки с 11 по 25, объявляет объект <xref:System.Windows.Data.ObjectDataProvider> с именем `LoadedBooks`, использующий в качестве источника элемент <xref:System.Xml.Linq.XElement>. Для инициализации этого <xref:System.Xml.Linq.XElement> проводится анализ встроенного XML-документа (элемент `CDATA`). Обратите внимание, что при объявлении и синтаксическом анализе внедренного XML-документа пробелы сохраняются. Это нужно потому, что элемент управления <xref:System.Windows.Controls.TextBlock>, используемый для отображения необработанного XML, не располагает возможностями для форматирования XML.  
  
 Наконец, в строках с 28 по 34 определяется <xref:System.Windows.DataTemplate> с именем `BookTemplate`. Он предназначен для отображения записей в разделе пользовательского интерфейса **Список книг** . В нем используются привязка данных и динамические свойства LINQ to XML для получения идентификатора книги с помощью следующих присваиваний.  
  
```  
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"  
```  
  
## <a name="data-binding-code"></a>Код привязки данных  
 Помимо элемента <xref:System.Windows.DataTemplate>, привязка данных используется во многих других местах файла.  
  
 В открывающем теге `<StackPanel>` в строке 38 для свойства <xref:System.Windows.FrameworkElement.DataContext%2A> этой панели устанавливается значение поставщика данных `LoadedBooks`.  
  
```  
DataContext="{Binding Source={StaticResource LoadedBooks}}  
```  
  
 Это позволяет далее (в строке 46) отобразить необработанный XML в объекте <xref:System.Windows.Controls.TextBlock> с именем `tbRawXml`, выполнив привязку к этому свойству поставщика данных `Xml`.  
  
```  
Text="{Binding Path=Xml}"   
```  
  
 Объект <xref:System.Windows.Controls.ListBox>, расположенный в разделе интерфейса **Список книг**, для своих отображаемых элементов задает в строках с 58 по 62 шаблон `BookTemplate`, определенный в разделе ресурсов окна.  
  
```  
ItemTemplate ="{StaticResource BookTemplate}"   
```  
  
 Затем в строках с 59 по 62 действительные значения книг привязываются к данному списку.  
  
```  
<ListBox.ItemsSource>  
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>  
</ListBox.ItemsSource>  
```  
  
 Третий раздел пользовательского интерфейса с названием **Редактировать выбранную книгу** прежде всего выполняет привязку элемента <xref:System.Windows.FrameworkElement.DataContext%2A> из родительского раздела <xref:System.Windows.Controls.StackPanel> к элементу, выбранному в разделе **Список книг** (строка 82).  
  
```  
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"  
```  
  
 Затем в нем используется двухсторонняя привязка данных, что позволяет отображать и обновлять текущие значения элементов книги с помощью двух текстовых полей данной панели. Привязка данных к динамическим свойствам аналогична используемой в шаблоне данных `BookTemplate` :  
  
```  
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"  
```  
  
 В XAML-коде последнего раздела пользовательского интерфейса, **Добавить новую книгу**, не используется привязка данных; вместо этого указанный код можно найти в его собственном коде обработки событий в файле L2DBForm.xaml.cs.  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
  
> [!NOTE]
>  Рекомендуется скопировать расположенный ниже код в редактор кода, например редактор исходного кода C# в Visual Studio, чтобы было легче отслеживать номера строк.  
  
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
 Сведения об исходном коде C# для обработчиков событий, связанных с элементами интерфейса WPF, см. в статье [L2DBForm.xaml.cs Source Code](../designers/l2dbform-xaml-cs-source-code.md) (Исходный код L2DBForm.xaml.cs).  
  
## <a name="see-also"></a>См. также  
 [Walkthrough: LinqToXmlDataBinding Example](../designers/walkthrough-linqtoxmldatabinding-example.md)  (Пошаговое руководство. Пример LinqToXmlDataBinding)  
 [Исходный код L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)
