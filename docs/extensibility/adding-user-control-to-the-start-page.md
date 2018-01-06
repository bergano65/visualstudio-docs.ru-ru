---
title: "Добавление пользовательского элемента управления на начальную страницу | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 448eba0d13a9501c328da79fa31fa66f4376d5df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="adding-user-control-to-the-start-page"></a>Добавление пользовательского элемента управления на начальную страницу
В этом пошаговом руководстве показано, как добавить ссылку на пользовательскую страницу DLL. В примере добавляется пользовательский элемент управления в решение создает пользовательский элемент управления, а затем ссылается на сборки из XAML-файл начальной страницы. Пользовательский элемент управления, который действует как простого веб-браузера, размещается на новой вкладке.  
  
 Чтобы добавить любую сборку, могут быть вызваны из XAML-файл можно использовать тот же процесс.  
  
## <a name="adding-a-wpf-user-control-to-the-solution"></a>Добавление пользовательского элемента управления WPF в решение  
 Во-первых добавьте в решение начальной страницы пользовательского элемента управления Windows Presentation Foundation (WPF).  
  
1.  Создание начальной страницы с помощью мы создали [Создание настраиваемая начальная страница](../extensibility/creating-a-custom-start-page.md).  
  
2.  В **обозревателе решений**, щелкните правой кнопкой мыши решение, нажмите кнопку **добавить**, а затем нажмите кнопку **новый проект**.  
  
3.  В левой области **новый проект** диалогового окна разверните **Visual Basic** или **Visual C#** и щелкните **Windows**. В средней области выберите **Библиотека пользовательских элементов управления WPF**.  
  
4.  Имя элемента управления `WebUserControl` и нажмите кнопку **ОК**.  
  
## <a name="implementing-the-user-control"></a>Реализация пользовательского элемента управления  
 Чтобы реализовать пользовательский элемент управления WPF, создайте пользовательский интерфейс (UI) в XAML, а затем написать события кода в C# или другой язык .NET.  
  
#### <a name="to-write-the-xaml-for-the-user-control"></a>Для записи XAML для пользовательского элемента управления  
  
1.  Откройте файл XAML для пользовательского элемента управления. В \<сетки > элемента, добавьте следующие определения строк в элемент управления.  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  В главном `Grid` элемента, добавьте следующий `Grid` элемент, который содержит текстовое поле для ввода веб-адреса и кнопку для задания нового адреса.  
  
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
  
3.  Добавьте следующий фрейм высшего уровня `Grid` элемент сразу после `Grid` элемент, который содержит текстовое поле и кнопку.  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4.  В примере показан полный код XAML для пользовательского элемента управления.  
  
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
  
#### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Для записи событий кода для пользовательского элемента управления  
  
1.  Дважды щелкните в конструкторе XAML **задать адрес** добавлен в элемент управления button.  
  
     В редакторе кода откроется файл UserControl1.cs.  
  
2.  Добавьте в обработчик событий SetButton_Click следующим образом.  
  
    ```csharp  
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
  
     Этот код задает веб-адрес, определенный в текстовом поле как целевой для веб-браузера. Если адрес не является допустимым, код вызывает ошибку.  
  
3.  Также необходимо обработать событие WebFrame_Navigated:  
  
    ```csharp  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  Постройте решение.  
  
## <a name="adding-the-user-control-to-the-start-page"></a>Добавление пользовательского элемента управления на начальную страницу  
 Чтобы освободить этот элемент управления в проект начальной страницы в файле проекта начальной страницы, добавьте ссылку на новую библиотеку элементов управления. Затем можно добавить элемент управления в разметку XAML начальной страницы.  
  
1.  В **обозревателе решений**, в проект, щелкните правой кнопкой мыши **ссылки** и нажмите кнопку **добавить ссылку**.  
  
2.  На **проекты** выберите **элемент WebUserControl, после** и нажмите кнопку **ОК**.  
  
3.  В меню **Сборка** выберите **Собрать решение**.  
  
     Построение решения делает пользовательский элемент управления доступным IntelliSense для других файлов в решении.  
  
 Чтобы добавить элемент управления в разметку XAML начальной страницы, добавьте ссылку на сборку пространства имен, а затем поместить элемент управления на странице.  
  
#### <a name="to-add-the-control-to-the-markup"></a>Чтобы добавить элемент управления в разметку  
  
1.  В **обозревателе решений**, откройте XAML-файл начальной страницы.  
  
2.  В **XAML** панели, добавьте следующее объявление пространства имен верхнего уровня <xref:System.Windows.Controls.Grid> элемента.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  В **XAML** области прокрутки для \<сетки > раздела.  
  
     Раздел содержит <xref:System.Windows.Controls.TabControl> элемент в <xref:System.Windows.Controls.Grid> элемент.  
  
4.  Добавить \<TabControl > элемента, содержащего \<TabItem >, содержащий ссылку на пользовательский элемент управления.  
  
    ```xml  
  
    <TabItem Header="Web" Height="Auto">  
        <vsc:UserControl1 />  
    </TabItem>  
  
    ```  
  
 Теперь можно проверить элемент управления.  
  
## <a name="testing-a-manually-created-custom-start-page"></a>Тестирование созданного вручную настраиваемой начальной страницы  
  
1.  Скопируйте файл XAML и все вспомогательные текстовые файлы или разметки файлы, к **%USERPROFILE%\My документы\Visual Studio 2015\StartPages\\**  папки.  
  
2.  Если начальная страница ссылается на все элементы или типы в сборках, которые не установлены в Visual Studio, скопируйте сборки, а затем вставьте их в *папка установки Visual Studio***\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  Введите в командную строку Visual Studio **devenv/rootsuffix Exp** открыть экспериментальный экземпляр Visual Studio.  
  
4.  В экспериментальном экземпляре, перейдите в **Сервис / Параметры / Среда / запуска** и выберите файл XAML из **настроить начальную страницу** раскрывающегося списка.  
  
5.  В меню **Вид** выберите пункт **Начальная страница**.  
  
     Отображать вашей настраиваемой начальной страницы. Если вы хотите изменить все файлы, необходимо Закройте экспериментальный экземпляр, внести изменения, скопируйте и вставьте измененных файлов и повторно открыть экспериментальный экземпляр, чтобы просмотреть изменения.  
  
## <a name="see-also"></a>См. также  
 [Контейнерные элементы управления WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)   
 [Пошаговое руководство. Добавление настраиваемого XAML-файла на начальную страницу](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)