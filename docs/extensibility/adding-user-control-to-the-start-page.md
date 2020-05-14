---
title: Добавление элемента управления пользователями в стартовую страницу (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b426cfbbfca2e301797644a1fc73f188054d0cfa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740127"
---
# <a name="add-user-control-to-the-start-page"></a>Добавление элемента управления пользователем в страницу «Старт»

В этом пошаговом показании, как добавить ссылку DLL на пользовательскую страницу Start Page. Пример добавляет элемент управления пользователя в решение, создает элемент управления пользователя, а затем ссылается на построенную сборку из файла Start Page *.xaml.* Новая вкладка размещает пользовательский контроль, который функционирует как базовый веб-браузер.

Вы можете использовать тот же процесс, чтобы добавить любую сборку, которая может быть вызвана из *файла .xaml.*

## <a name="add-a-wpf-user-control-to-the-solution"></a>Добавление элемента управления пользователем WPF в решение

Во-первых, добавьте управление пользователями Фонда презентации Windows (WPF) в решение Start Page.

1. Создайте стартовую страницу, используя созданный для [создания пользовательской стартовой страницы.](../extensibility/creating-a-custom-start-page.md)

2. В **Solution Explorer**, правой кнопкой мыши решение, нажмите **Добавить**, а затем нажмите **Новый проект**.

3. В левом стекле диалогового окна **Нового проекта** расширьте либо visual **Basic,** либо визуальный узла **C',** а также нажмите **на Windows.** В середине панели выберите **библиотеку управления пользователями WPF.**

4. Назовите элемент управления, `WebUserControl` а затем нажмите **OK**.

## <a name="implement-the-user-control"></a>Реализация пользовательского контроля

Чтобы реализовать пользовательский контроль WPF, создайте пользовательский интерфейс (UI) в XAML, а затем напишите события сзади кода на языке C- или другом языке .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Для записи XAML для управления пользователем

1. Откройте файл XAML для управления пользователем. В `<Grid>` элементе добавьте следующие определения строки в элемент управления.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. В основной `<Grid>` элемент добавьте `<Grid>` следующий новый элемент, содержащий текстовый ящик для ввода веб-адресов и кнопку для настройки нового адреса.

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

3. Добавьте следующий кадр к `<Grid>` элементу `<Grid>` верхнего уровня сразу после элемента, содержащего кнопку и текстовый ящик.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. Ниже приводится следующий пример завершения XAML для управления пользователем.

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

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Запись событий, лежащих в основе кода, для управления пользователем

1. В конструкторе XAML дважды щелкните кнопку **Set Address,** добавленную в управление.

    Файл *UserControl1.cs* открывается в редакторе кода.

2. Заполните обработчик SetButton_Click события следующим образом.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
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

    Этот код устанавливает веб-адрес, который вводится в текстовое поле в качестве цели для веб-браузера. Если адрес недействителен, код бросает ошибку.

3. Вы также должны справиться с WebFrame_Navigated событием:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Создайте решение.

## <a name="add-the-user-control-to-the-start-page"></a>Добавление элемента управления пользователем в страницу «Старт»

Чтобы сделать этот элемент доступным для проекта «Старт Пейдж» в файле проекта «Старт-страница», добавьте ссылку на новую библиотеку управления. Затем можно добавить элемент управления в разметку Start Page XAML.

1. В **Solution Explorer**, в проекте Start Page, ссылки на кнопку «Правой **кнопки»,** а затем нажмите **Добавить справку.**

2. На вкладке **«Проекты»** выберите **WebUserControl,** а затем нажмите **OK.**

3. В меню **Сборка** выберите **Построить решение**.

    Создание решения делает пользовательский контроль доступным для IntelliSense для других файлов в решении.

    Чтобы добавить элемент управления в разметку Start Page XAML, добавьте ссылку на пространство имен в сборку, а затем поместите элемент управления на страницу.

### <a name="to-add-the-control-to-the-markup"></a>Добавление элемента управления в разметку

1. В **Solution Explorer**откройте файл Start Page *.xaml.*

2. В панели **XAML** добавьте следующее объявление пространства имен <xref:System.Windows.Controls.Grid> в элемент верхнего уровня.

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. В панели **XAML** прокрутите раздел \<Grid>.

    Раздел содержит <xref:System.Windows.Controls.TabControl> элемент в <xref:System.Windows.Controls.Grid> элементе.

4. Добавьте \<элемент TabControl \<>, содержащий> TabItem, содержащий ссылку на пользовательский контроль.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Теперь вы можете проверить управление.

## <a name="test-a-manually-created-custom-start-page"></a>Проверьте созданную вручную пользовательскую страницу Start Page

1. Копируйте свой файл XAML, а также любые вспомогательные текстовые файлы или файлы разметки, в *"%USERPROFILE%"Мои документы-Visual Studio 2015-StartPages\\ * папку.

2. Если ваша стартовая страница ссылается на любые элементы управления или типы в сборках, которые не установлены Visual Studio, скопируйте сборки, а затем вставьте их в _папку установки Visual Studio_**\\.**

3. В команде Visual Studio введите **devenv/rootsuffix Exp,** чтобы открыть экспериментальный экземпляр Visual Studio.

4. В экспериментальном примере перейдите на страницу**запуска**  > **среды** > параметры > **инструментов**и выберите файл XAML из момента отбрасывания **стартовой страницы.** **Tools**

5. В меню **Вид** выберите пункт **Начальная страница**.

    Ваша пользовательская стартовая страница должна отображаться. Если требуется изменить любые файлы, необходимо закрыть экспериментальный экземпляр, внести изменения, скопировать и вставить измененные файлы, а затем повторно открыть экспериментальный экземпляр для просмотра изменений.

## <a name="see-also"></a>См. также

- [Контроль контейнеров WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [Прохождение: Добавить пользовательский XAML на стартовую страницу](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
