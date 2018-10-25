---
title: Добавление пользовательского элемента управления на начальную страницу | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 40d508a11807fe90981104e0cc7e6557577da103
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855603"
---
# <a name="adding-user-control-to-the-start-page"></a>Добавление пользовательского элемента на начальную страницу
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как добавить ссылку на библиотеку DLL для настраиваемой начальной страницы. В примере добавляется пользовательский элемент управления в решение сборки пользовательского элемента управления, а затем ссылается на сборку из XAML-файл начальной страницы. Пользовательский элемент управления, который функционирует как базовый веб-браузер, размещается на новой вкладке.  
  
 Чтобы добавить любую сборку, могут вызываться из XAML-файла можно использовать тот же процесс.  
  
## <a name="adding-a-wpf-user-control-to-the-solution"></a>Добавление пользовательского элемента управления WPF в решение  
 Во-первых добавьте пользовательский элемент управления Windows Presentation Foundation (WPF) к решению для начальной страницы.  
  
1.  Создание начальной страницы с помощью мы создали в [Создание настраиваемая начальная страница](../extensibility/creating-a-custom-start-page.md).  
  
2.  В **обозревателе решений**, щелкните правой кнопкой мыши решение, нажмите кнопку **добавить**, а затем нажмите кнопку **новый проект**.  
  
3.  В левой области **новый проект** диалогового окна разверните узел, либо **Visual Basic** или **Visual C#** и щелкните **Windows**. В средней области выберите **Библиотека пользовательских элементов управления WPF**.  
  
4.  Назовите элемент управления `WebUserControl` и нажмите кнопку **ОК**.  
  
## <a name="implementing-the-user-control"></a>Реализация пользовательского элемента управления  
 Чтобы реализовать пользовательский элемент управления WPF, построения пользовательского интерфейса (UI) в XAML и затем записывают события кода на C# или другом языке .NET.  
  
#### <a name="to-write-the-xaml-for-the-user-control"></a>Для записи XAML для пользовательского элемента управления  
  
1.  Откройте файл XAML для пользовательского элемента управления. В \<сетки > элемента, добавьте следующие определения строк к элементу управления.  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  В главном `Grid` элемента, добавьте следующий новый `Grid` элемент, который содержит текстовое поле для ввода веб-адреса и кнопку для задания нового адреса.  
  
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
  
3.  Добавьте следующий фрейм высшего уровня `Grid` элемент сразу после `Grid` элемент, содержащий текстовое поле и кнопку.  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4.  В следующем примере показано завершенное XAML для пользовательского элемента управления.  
  
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
  
1.  В конструкторе XAML, дважды щелкните **Set Address** кнопкой, добавленными к элементу управления.  
  
     В редакторе кода откроется файл UserControl1.cs.  
  
2.  Заполните SetButton_Click обработчик событий следующим образом.  
  
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
  
     Этот код задает веб-адрес, введенный в текстовом поле как целевой для веб-браузера. Если адрес не является допустимым, код вызывает ошибку.  
  
3.  Также необходимо обрабатывать событие WebFrame_Navigated:  
  
    ```csharp  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  Постройте решение.  
  
## <a name="adding-the-user-control-to-the-start-page"></a>Добавление пользовательского элемента управления на начальную страницу  
 Чтобы сделать этот элемент управления доступным в проект начальной страницы в файле проекта начальной страницы, добавьте ссылку в новой библиотеки элементов управления. Затем можно добавить элемент управления к разметке запуск страницы XAML.  
  
1. В **обозревателе решений**, в проект, щелкните правой кнопкой мыши **ссылки** и нажмите кнопку **добавить ссылку**.  
  
2. На **проекты** выберите **элемент WebUserControl, после** и нажмите кнопку **ОК**.  
  
3. В меню **Сборка** выберите **Собрать решение**.  
  
    Построение решения делает пользовательский элемент управления доступным для IntelliSense для других файлов в решении.  
  
   Добавление элемента управления в разметку XAML страницы запуска, добавьте ссылку на сборку пространства имен, а затем разместите элемент управления на странице.  
  
#### <a name="to-add-the-control-to-the-markup"></a>Добавление элемента управления к разметке  
  
1. В **обозревателе решений**, откройте XAML-файл начальной страницы.  
  
2. В **XAML** панель, добавьте следующее объявление пространства имен верхнего уровня <xref:System.Windows.Controls.Grid> элемент.  
  
   ```xml  
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
   ```  
  
3. В **XAML** панели, прокрутите вниз до \<сетки > раздела.  
  
    В разделе содержатся <xref:System.Windows.Controls.TabControl> элемент в <xref:System.Windows.Controls.Grid> элемент.  
  
4. Добавить \<TabControl > элемента, содержащего \<TabItem >, содержащий ссылку на пользовательский элемент управления.  
  
   ```xml  
  
   <TabItem Header="Web" Height="Auto">  
       <vsc:UserControl1 />  
   </TabItem>  
  
   ```  
  
   Теперь можно протестировать элемент управления.  
  
## <a name="testing-a-manually-created-custom-start-page"></a>Тестирование созданного вручную настраиваемой начальной страницы  
  
1.  Скопируйте файл XAML и все вспомогательные текстовые файлы или разметки файлы, к **%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\**  папки.  
  
2.  Если начальная страница ссылается на все элементы или типы в сборках, которые не установлены в Visual Studio, скопируйте сборки, а затем вставьте их в _папка установки Visual Studio_**\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  В командной строке Visual Studio, введите **devenv/rootsuffix Exp** открыть экспериментальный экземпляр Visual Studio.  
  
4.  В экспериментальном экземпляре выберите **Сервис / Параметры / Среда / запуска** страницы и выберите свой файл XAML из **настроить начальную страницу** раскрывающегося списка.  
  
5.  В меню **Вид** выберите пункт **Начальная страница**.  
  
     Отображать пользовательской начальной страницы. Если вы хотите изменить любые файлы, необходимо закрыть экспериментальный экземпляр, внесите изменения, скопируйте и вставьте измененных файлов и повторно открыть экспериментальный экземпляр, чтобы просмотреть изменения.  
  
## <a name="see-also"></a>См. также  
 [Контейнерные элементы управления WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)   
 [Пошаговое руководство. Добавление настраиваемого XAML-файла на начальную страницу](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)

