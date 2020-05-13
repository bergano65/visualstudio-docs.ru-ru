---
title: 'Прохождение: Сохранение настроек пользователя на стартовой странице (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8c791bb33d6c6a3952c14d5073857b0c3131cecf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697079"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Прохождение: Сохранение настроек пользователя на стартовой странице

Можно сохранять настройки пользователя для стартовой страницы. Следуя этому пошаговому шагу, можно создать элемент управления, который сохраняет настройку в реестре, когда пользователь нажимает кнопку, а затем получает эту настройку каждый раз, когда загружается стартовая страница. Поскольку шаблон проекта Start Page включает в себя настраиваемый пользовательский контроль, а по умолчанию Начинается XAML вызовы, которые контролируют, вам не нужно изменять саму стартовую страницу.

Хранилище настроек, мгновенно евращенное в этом <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> пошаговом пошаговом письме, является экземпляром интерфейса, который читает и записывает в следующее место регистрации, когда он называется: **HKCU-Software-Microsoft-Visual>Studio\\\<**

Когда он работает в экспериментальном экземпляре Visual Studio, магазин настроек читает и записывает в **HKCU-Software-Microsoft-VisualStudio-14.0Exp\\\<CollectionName>.**

Для получения дополнительной информации о том, как упорствовать в настройках, [см.](../extensibility/extending-user-settings-and-options.md)

## <a name="prerequisites"></a>Предварительные требования

> [!NOTE]
> Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации, [см.](../extensibility/visual-studio-sdk.md)
>
> Вы можете скачать шаблон проекта Start Page с помощью **менеджера расширения.**

## <a name="set-up-the-project"></a>Настройка проекта

1. Создайте проект «Старт-страницы», описанный в [«Создать пользовательскую стартовую страницу».](creating-a-custom-start-page.md) Назовите проект **SaveMySettings**.

2. В **Solution Explorer**добавьте следующие ссылки на сборку проекта StartPageControl:

    - EnvDTE

    - EnvDTE80

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. Открыть *MyControl.xaml*.

4. Из панели XAML в определении <xref:System.Windows.Controls.UserControl> элемента верхнего уровня добавьте следующую декларацию событий после деклараций пространства имен.

    ```xml
    Loaded="OnLoaded"
    ```

5. В панели дизайна щелкните основную область управления, а затем нажмите **Удалить**.

     Этот шаг удаляет <xref:System.Windows.Controls.Border> элемент и все в нем, <xref:System.Windows.Controls.Grid> и оставляет только элемент верхнего уровня.

6. Из **toolbox**перетащите <xref:System.Windows.Controls.StackPanel> элемент управления в сетку.

7. Теперь <xref:System.Windows.Controls.TextBlock>перетащите <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.StackPanel>, а, и кнопку в .

8. Добавьте атрибут **x:Name** для <xref:System.Windows.Controls.TextBox> `Click` , и <xref:System.Windows.Controls.Button>событие для , как показано в следующем примере.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Реализация пользовательского контроля

1. В панели XAML щелкните `Click` по <xref:System.Windows.Controls.Button> элементу справа, а затем нажмите **«Перейдите к обработчику событий».**

     Этот шаг открывает *MyControl.xaml.cs*и создает обработчик заглушки для `Button_Click` события.

2. Добавьте `using` следующие директивы в верхнюю часть файла.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Добавьте `SettingsStore` частную собственность, как показано в следующем примере.

    ```csharp
    private IVsWritableSettingsStore _settingsStore = null;
    private IVsWritableSettingsStore SettingsStore
    {
        get
        {
            if (_settingsStore == null)
            {
                // Get a reference to the DTE from the DataContext.
                var typeDescriptor = DataContext as ICustomTypeDescriptor;
                var propertyCollection = typeDescriptor.GetProperties();
                var dte = propertyCollection.Find("DTE", false).GetValue(
                    DataContext) as DTE2;

                // Get the settings manager from the DTE.
                var serviceProvider = new ServiceProvider(
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
                var settingsManager = serviceProvider.GetService(
                    typeof(SVsSettingsManager)) as IVsSettingsManager;

                // Write the user settings to _settingsStore.
                settingsManager.GetWritableSettingsStore(
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,
                    out _settingsStore);
            }
            return _settingsStore;
        }
    }
    ```

     Это свойство сначала получает <xref:EnvDTE80.DTE2> ссылку на интерфейс, который <xref:System.Windows.FrameworkElement.DataContext%2A> содержит модель объекта автоматизации, от управления пользователем, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> а затем использует DTE, чтобы получить экземпляр интерфейса. Затем он использует этот экземпляр для возврата текущих настроек пользователя.

4. Заполните `Button_Click` событие следующим образом.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        int exists = 0;
        SettingsStore.CollectionExists("MySettings", out exists);
        if (exists != 1)
        {
            SettingsStore.CreateCollection("MySettings");
        }
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);
    }
    ```

     Это записывает содержание текстового поля в поле "MySetting" в коллекции "MySettings" в реестре. Если коллекция не существует, она создана.

5. Добавьте следующий `OnLoaded` обработчик для случая управления пользователем.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Этот код устанавливает текст текстового окна к текущему значению "MySetting".

6. Создайте пользовательский контроль.

7. В **Solution Explorer**, с открытым *исходным кодом.extension.vsixmanifest*.

8. В явном редакторе установите **имя продукта,** чтобы **сохранить мои настройки Начало страницы**.

     Эта функция устанавливает имя стартовой страницы, как это, чтобы появиться в списке **настроить Start Page** в поле диалога **опционов.**

9. Построить *StartPage.xaml*.

## <a name="test-the-control"></a>Тестирование элемента управления

1. Нажмите клавишу **F5**.

     Открывается экспериментальный экземпляр Visual Studio.

2. В экспериментальном примере, в меню **Tools,** нажмите **Параметры**.

3. В узло **среды** щелкните **Startup,** а затем, в списке **настраиваемых стартовых страниц,** выберите **«Установленное расширение» Сохранить мои настройки Начало страницы.**

     Нажмите кнопку **ОК**.

4. Закройте стартовую страницу, если она открыта, а затем, в меню **Просмотра,** нажмите **«Стартовая страница».**

5. На стартовой странице щелкните на вкладке **MyControl.**

6. В текстовом поле, введите **Cat**, а затем нажмите **Сохранить мою настройку**.

7. Закройте стартовую страницу, а затем откройте ее снова.

     Слово "кошка" должно отображаться в текстовом окне.

8. Замените слово "кошка" словом "Собака". Не нажимайте на кнопку.

9. Закройте стартовую страницу, а затем откройте ее снова.

     Слово "Собака" должно отображаться в текстовом поле, даже если вы не сохранили настройки, потому что Visual Studio сохраняет окна инструментов в памяти, даже если они закрыты, пока Visual Studio сама закрывается.

10. Закройте экспериментальный экземпляр Visual Studio.

11. Нажмите **F5,** чтобы вновь открыть экспериментальный экземпляр.

12. Слово "кошка" должно отображаться в текстовом окне.

## <a name="next-steps"></a>Следующие шаги

Вы можете изменить этот пользовательский элемент управления, чтобы сохранить и получить любое количество пользовательских `SettingsStore` настроек, используя различные значения из различных обработчиков событий, чтобы получить и установить свойство. До тех пор, `propertyName` как вы используете другой параметр для каждого <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>вызова, значения не перезавершать друг друга в реестре.

## <a name="see-also"></a>См. также

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Добавление команд Visual Studio в стартовую страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
