---
title: "Добавление пользовательского элемента управления на страницу Пуск | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 69c2ff24616af373461de0cbf4456499db63f902
ms.lasthandoff: 02/22/2017

---
# <a name="adding-user-control-to-the-start-page"></a>Добавление пользовательского элемента управления к домашней странице
В этом пошаговом руководстве показано, как добавить ссылку на пользовательскую страницу DLL. В примере добавляется пользовательский элемент управления в решение сборки пользовательского элемента управления, а затем ссылается на сборку из XAML-файл начальной страницы. Пользовательский элемент управления, который работает как простого веб-браузера, размещается на новой вкладке.  
  
 Для добавления любой сборки, который можно вызвать из файла XAML можно использовать тот же процесс.  
  
## <a name="adding-a-wpf-user-control-to-the-solution"></a>Добавление пользовательского элемента управления WPF в решение  
 Во-первых добавьте пользовательский элемент управления Windows Presentation Foundation (WPF) в решение начальной страницы.  
  
1.  Создание домашней страницы с помощью созданной в [Создание начальной страницы пользовательских](../extensibility/creating-a-custom-start-page.md).  
  
2.  В **обозревателе решений**, щелкните правой кнопкой мыши решение, нажмите кнопку **добавить**, а затем нажмите кнопку **новый проект**.  
  
3.  В левой области **новый проект** диалогового окна разверните **Visual Basic** или **Visual C#** и выберите команду **Windows**. В средней области выберите **Библиотека пользовательских элементов управления WPF**.  
  
4.  Имя элемента управления `WebUserControl` и нажмите кнопку **ОК**.  
  
## <a name="implementing-the-user-control"></a>Реализация пользовательского элемента управления  
 Чтобы реализовать пользовательский элемент управления WPF, создавать пользовательский интерфейс (UI) в XAML, а затем написать события кода на C# или другом языке .NET.  
  
#### <a name="to-write-the-xaml-for-the-user-control"></a>Для записи XAML для пользовательского элемента управления  
  
1.  Откройте XAML-файл пользовательского элемента управления. В \<Сетка настроек элемента, добавьте следующие определения строк в элемент управления.  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  В главном `Grid` элемента, добавьте следующий `Grid` элемент, который содержит текстовое поле для ввода веб-адресов и кнопку для задания нового адреса.  
  
    ```xml  
    <Grid Grid.Row="0">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="*" />  
            <ColumnDefinition Width="Auto" />  
        </Grid.ColumnDefinitions>  
        <TextBox x:Name="UserSource" Grid.Column="0" />  
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />  
    </Grid>  
    ```  
  
3.  Добавьте следующий фрейм верхнего уровня `Grid` элемент сразу после `Grid` элемент, содержащий текстовое поле и кнопку.  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4.  Следующий пример показывает завершенный XAML для пользовательского элемента управления.  
  
    ```xml  
    <UserControl x:Class="WebUserControl.UserControl1"  
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
                 mc:Ignorable="d"   
                 d:DesignHeight="300" d:DesignWidth="300">  
        <Grid>  
            <Grid.RowDefinitions>  
                <RowDefinition Height="Auto"/>  
                <RowDefinition Height="*" />  
            </Grid.RowDefinitions>  
            <Grid Grid.Row="0">  
                <Grid.ColumnDefinitions>  
                    <ColumnDefinition Width="*" />  
                    <ColumnDefinition Width="Auto" />  
                </Grid.ColumnDefinitions>  
                <TextBox x:Name="UserSource" Grid.Column="0" />  
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />  
            </Grid>  
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
        </Grid>  
    </UserControl>  
  
    ```  
  
#### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Для записи событий фонового кода для пользовательского элемента управления  
  
1.  Дважды щелкните в конструкторе XAML **Set Address** кнопкой, добавленными к элементу управления.  
  
     В редакторе кода откроется файл UserControl1.cs.  
  
2.  Заполните SetButton_Click обработчик событий следующим образом.  
  
    ```c#  
    private void SetButton_Click(object sender, RoutedEventArgs e)  
    {  
        try  
        {  
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);  
        }  
        catch (Exception error)  
        {  
            MessageBox.Show(error.Message);  
        }  
    }  
    ```  
  
     Этот код задает веб-адрес, который типизируется как целевой для веб-браузера в текстовом поле. Если адрес не является допустимым, код вызывает ошибку.  
  
3.  Также необходимо обработать событие WebFrame_Navigated:  
  
    ```c#  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  Постройте решение.  
  
## <a name="adding-the-user-control-to-the-start-page"></a>Добавление пользовательского элемента управления к домашней странице  
 Чтобы сделать этот элемент доступным в проекте начальной страницы в файле проекта начальной страницы, добавьте ссылку на новую библиотеку элементов управления. Затем можно добавить элемент управления в разметку XAML начальной страницы.  
  
1.  В **обозревателе решений**, в проект, щелкните правой кнопкой мыши **ссылки** и нажмите кнопку **добавить ссылку**.  
  
2.  На **проекты** выберите **элемент WebUserControl, после** и нажмите кнопку **ОК**.  
  
3.  В меню **Сборка** выберите **Собрать решение**.  
  
     Построение решения предоставляет пользовательский элемент управления доступные технологии IntelliSense для других файлов в решении.  
  
 Чтобы добавить элемент управления в разметку XAML начальной страницы, добавьте ссылку на сборку пространства имен, а затем разместите элемент управления на странице.  
  
#### <a name="to-add-the-control-to-the-markup"></a>Чтобы добавить элемент управления в разметку  
  
1.  В **обозревателе**, откройте XAML-файл начальной страницы.  
  
2.  В **XAML** области, добавьте следующее объявление пространства имен верхнего уровня <xref:System.Windows.Controls.Grid>элемент.</xref:System.Windows.Controls.Grid>  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  В **XAML** область, перейдите к \<сетке настроек раздела.  
  
     Раздел содержит <xref:System.Windows.Controls.TabControl>элемент в <xref:System.Windows.Controls.Grid>элемент.</xref:System.Windows.Controls.Grid> </xref:System.Windows.Controls.TabControl>  
  
4.  Добавить \<TabControl настроек элемента, содержащего \<TabItem настроек, содержащий ссылку на пользовательский элемент управления.  
  
    ```xml  
  
    <TabItem Header="Web" Height="Auto">  
        <vsc:UserControl1 />  
    </TabItem>  
  
    ```  
  
 Теперь можно проверить элемент управления.  
  
## <a name="testing-a-manually-created-custom-start-page"></a>Тестирование созданного вручную настроенную начальную страницу  
  
1.  Скопируйте файл XAML и любые вспомогательные текстовые файлы или разметки файлы, в **%USERPROFILE%\My 2015\StartPages документы\Visual Studio\\ ** папки.  
  
2.  Если стартовая страница ссылается на все элементы или типы в сборках, которые не установлены в Visual Studio, скопируйте сборки и затем вставить их в *папка установки Visual Studio***\Common7\IDE\PrivateAssemblies\\**.  
  
3.  Введите в командную строку Visual Studio **devenv/rootsuffix Exp** открываемого в экспериментальном экземпляре Visual Studio.  
  
4.  В экспериментальном экземпляре, перейдите к **Сервис / Параметры / среды и запуска** и выберите свой XAML-файл из **настроить начальную страницу** раскрывающегося списка.  
  
5.  В меню **Вид** выберите пункт **Начальная страница**.  
  
     Отображать пользовательской начальной страницы. Если вы хотите изменить любые файлы, необходимо Закройте экспериментальный экземпляр, внесите необходимые изменения, скопируйте и вставьте измененных файлов и повторно открыть экспериментальный экземпляр для просмотра изменений.  
  
## <a name="see-also"></a>См. также  
 [Контейнерные элементы управления WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)   
 [Пошаговое руководство: Добавление пользовательского XAML-файла начальной страницы](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
