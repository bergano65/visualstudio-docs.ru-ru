---
title: "Пошаговое руководство: Сохранение пользовательских параметров на начальной странице | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a7d8649e0d8cf83650da58386901e638ec14a2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>Пошаговое руководство: Сохранение пользовательских параметров на начальной странице
Можно сохранить пользовательские параметры для Начальная страница. С помощью этого пошагового руководства, можно создать элемент управления, который сохраняет параметр в реестре, когда пользователь нажимает кнопку, а затем извлекает задание каждый раз при загрузке начальной страницы. Шаблон проекта начальной страницы включает в себя настраиваемый пользовательский элемент управления, и этот элемент управления вызывает XAML начальной страницы по умолчанию, у вас сам изменение начальной страницы.  
  
 Хранилище настроек, экземпляр которого создается в этом пошаговом руководстве представляет собой экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> интерфейс, который считывает и записывает в следующий раздел реестра, при вызове: HKCU\Software\Microsoft\VisualStudio\14.0\\  *Имя_коллекции*  
  
 При выполнении в экспериментальном экземпляре Visual Studio, параметры хранилища считывает и записывает HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*CollectionName.*  
  
 Дополнительные сведения о том, как сохранить параметры в разделе [расширение настройки пользователя и параметры](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
  
> [!NOTE]
>  Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
>   
>  Можно загрузить с помощью шаблона проекта начальной страницы **Диспетчер расширений**.  
  
## <a name="setting-up-the-project"></a>Настройка проекта  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>Настройка проекта для данного пошагового руководства  
  
1.  Создайте проект начальной страницы, как описано в [Создание настраиваемая начальная страница](creating-a-custom-start-page.md). Назовите проект **SaveMySettings**.  
  
2.  В **обозревателе решений**, добавьте следующие ссылки в проект StartPageControl:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  Откройте файл MyControl.xaml.  
  
4.  XAML, в области верхнего уровня <xref:System.Windows.Controls.UserControl> определение элемента, добавьте следующее объявление события после объявления пространства имен.  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  В области конструктора щелкните область основного элемента управления и нажмите клавишу DELETE.  
  
     Эта функция удаляет <xref:System.Windows.Controls.Border> элемент и все объекты и оставляет только верхнего уровня <xref:System.Windows.Controls.Grid> элемента.  
  
6.  Из **элементов**, перетащите <xref:System.Windows.Controls.StackPanel> элемента управления в сетке.  
  
7.  Теперь перетащите <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox>и кнопка для <xref:System.Windows.Controls.StackPanel>.  
  
8.  Добавить **x: Name** для атрибута <xref:System.Windows.Controls.TextBox>и `Click` событий для <xref:System.Windows.Controls.Button>, как показано в следующем примере.  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>Реализация пользовательского элемента управления  
  
#### <a name="to-implement-the-user-control"></a>Для реализации пользовательского элемента управления  
  
1.  Щелкните правой кнопкой мыши в области XAML `Click` атрибут <xref:System.Windows.Controls.Button> элемент, а затем щелкните **к обработчику событий**.  
  
     Это открывает MyControl.xaml.cs и создает обработчик заглушки для `Button_Click` события.  
  
2.  Добавьте следующие `using` инструкции в начало файла.  
  
     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  Добавьте закрытый `SettingsStore` свойства, как показано в следующем примере.  
  
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
  
     Это свойство сначала получает ссылку на <xref:EnvDTE80.DTE2> интерфейс, который содержит объектную модель автоматизации из <xref:System.Windows.FrameworkElement.DataContext%2A> из пользовательского элемента управления, а затем используется для получения экземпляра DTE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> интерфейса. Затем он использует этот экземпляр для возврата параметры текущего пользователя.  
  
4.  Заполните `Button_Click` событие следующим образом.  
  
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
  
     Записывает содержимое текстового поля к полю «MySetting» в коллекции «MySettings» в реестре. Если коллекция не существует, он создается.  
  
5.  Добавьте следующий обработчик для `OnLoaded` события пользовательского элемента управления.  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     Это задает текст текстового поля в текущее значение «MySetting».  
  
6.  Построение пользовательского элемента управления.  
  
7.  В **обозревателе решений**, откройте файл source.extension.vsixmanifest.  
  
8.  В редакторе манифестов задать **название продукта** для **сохранить мои параметры начальной страницы**.  
  
     Таким образом задается имя начальной страницы как в **настроить начальную страницу** списка в **параметры** диалоговое окно.  
  
9. Создать файл StartPage.xaml.  
  
## <a name="testing-the-control"></a>Тестирование элемента управления  
  
#### <a name="to-test-the-user-control"></a>Для тестирования пользовательского элемента управления  
  
1.  Нажмите клавишу F5.  
  
     Откроется экспериментальный экземпляр Visual Studio.  
  
2.  В экспериментальном экземпляре на **средства** меню, нажмите кнопку **параметры**.  
  
3.  В **среды** узел, щелкните **запуска**, а затем в **настроить начальную страницу** выберите **[установленных расширений] сохранить мои параметры начальной страницы** .  
  
     Нажмите кнопку **ОК**.  
  
4.  Закройте начальной страницы, если он открыт, а затем на **представление** меню, нажмите кнопку **начальной страницы**.  
  
5.  На начальной странице щелкните **MyControl** вкладки.  
  
6.  В текстовом поле введите **Cat**, а затем нажмите кнопку **сохранить Мои параметр**.  
  
7.  Закройте страницу «Пуск» и откройте его снова.  
  
     Слова «Cat» должен отображаться в текстовом поле.  
  
8.  Замените слова «Cat» слово «Dog». Не нажимайте кнопку.  
  
9. Закройте страницу «Пуск» и откройте его снова.  
  
     Слово «Dog» должны отображаться в текстовом поле, несмотря на то, что параметр не был сохранен. Это происходит, поскольку Visual Studio сохраняет окна инструментов в памяти, даже если они были закрыты, пока не закрыт Visual Studio.  
  
10. Закройте экспериментальный экземпляр Visual Studio.  
  
11. Нажмите клавишу F5, чтобы снова открыть экспериментальный экземпляр.  
  
12. Слова «Cat» должен отображаться в текстовом поле.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 Вы можете изменить этот пользовательский элемент управления для сохранения и извлечения любое количество пользовательские параметры с помощью различных значений различные обработчики событий для получения и задания `SettingsStore` свойство. Поскольку можно использовать другой `propertyName` параметра для каждого вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, значения не будут перезаписывать друг с другом в реестре.  
  
## <a name="see-also"></a>См. также  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [Добавление команд Visual Studio на начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md)