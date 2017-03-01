---
title: "Пошаговое руководство: Сохранение пользовательских параметров на начальной странице | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: 18
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
ms.sourcegitcommit: c358bf79945b4f4eef5b19c60cad0bd866c175b3
ms.openlocfilehash: 1bf8a313898f9c12312beedb31238fb74e1a56a8
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>Пошаговое руководство: Сохранение пользовательских параметров на начальной странице
Можно сохранить пользовательские параметры для своей начальной страницы. В данном пошаговом руководстве, можно создать элемент управления, который сохраняет параметр в реестр, когда пользователь нажимает кнопку, а затем извлекает эту настройку, каждый раз при загрузке страницы запуска. Так как начальная страница шаблон проекта включает настраиваемый пользовательский элемент управления XAML начальной страницы по умолчанию вызывает этот элемент управления, у вас сам изменение начальной страницы.  
  
 Хранилище настроек, экземпляр которого создается в этом пошаговом руководстве является экземпляром класса <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>интерфейс, который считывает и записывает в следующий раздел реестра, при вызове: HKCU\Software\Microsoft\VisualStudio\14.0\\*ИмяКоллекции* </xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>  
  
 При работе в экспериментальном экземпляре Visual Studio, параметры хранилища считывает и записывает HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*ИмяКоллекции.*  
  
 Дополнительные сведения о том, как сохранить параметры в разделе [расширение настройки пользователя и параметры](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
  
> [!NOTE]
>  Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
>   
>  Начальная страница шаблона проекта можно загрузить с помощью **Диспетчер расширений**.  
  
## <a name="setting-up-the-project"></a>Настройка проекта  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>Настройка проекта для данного пошагового руководства  
  
1.  Создайте проект начальной страницы, как описано в [Создание начальной страницы пользовательских](creating-a-custom-start-page.md). Назовите проект **SaveMySettings**.  
  
2.  В **обозревателе**, добавьте следующие ссылки на сборки в проекте StartPageControl:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  Откройте файл MyControl.xaml.  
  
4.  XAML, в области верхнего уровня <xref:System.Windows.Controls.UserControl>Определение элемента, добавьте следующее объявление события после объявления пространств имен.</xref:System.Windows.Controls.UserControl>  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  В области конструктора щелкните основную область элемента управления и нажмите клавишу DELETE.  
  
     При этом удаляются <xref:System.Windows.Controls.Border>элемент и все, что и оставляет только верхнего уровня <xref:System.Windows.Controls.Grid>элемент.</xref:System.Windows.Controls.Grid> </xref:System.Windows.Controls.Border>  
  
6.  От **элементов**, перетащите <xref:System.Windows.Controls.StackPanel>управления в сетку.</xref:System.Windows.Controls.StackPanel>  
  
7.  Теперь перетащите <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox>и кнопка для <xref:System.Windows.Controls.StackPanel>.</xref:System.Windows.Controls.StackPanel> </xref:System.Windows.Controls.TextBox> </xref:System.Windows.Controls.TextBlock>  
  
8.  Добавить **x: Name** атрибут <xref:System.Windows.Controls.TextBox>и `Click` событие <xref:System.Windows.Controls.Button>, как показано в следующем примере.</xref:System.Windows.Controls.Button> </xref:System.Windows.Controls.TextBox>  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>Реализация пользовательского элемента управления  
  
#### <a name="to-implement-the-user-control"></a>Для реализации пользовательского элемента управления  
  
1.  Щелкните правой кнопкой мыши в области XAML `Click` атрибут <xref:System.Windows.Controls.Button>элемента, а затем щелкните **к обработчику событий**.</xref:System.Windows.Controls.Button>  
  
     Это открывает MyControl.xaml.cs и создает обработчик заглушки для `Button_Click` события.  
  
2.  Добавьте следующие `using` инструкции в начало файла.  
  
     [!code-cs[StartPageDTE&11;](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  Добавьте закрытый `SettingsStore` свойства, как показано в следующем примере.  
  
    ```c#  
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
  
     Это свойство сначала получает ссылку на <xref:EnvDTE80.DTE2>интерфейс, который содержит модель объектов автоматизации, <xref:System.Windows.FrameworkElement.DataContext%2A>пользовательский элемент управления, а затем использует DTE для получения экземпляра <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> </xref:System.Windows.FrameworkElement.DataContext%2A> </xref:EnvDTE80.DTE2> Затем он использует этот экземпляр для возврата параметры текущего пользователя.  
  
4.  Заполните `Button_Click` события, как показано ниже.  
  
    ```c#  
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
  
     Это записывает содержимое текстового поля к полю «MySetting» в коллекции «MySettings» в реестре. Если коллекция не существует, он создается.  
  
5.  Добавьте следующий обработчик `OnLoaded` событий пользовательского элемента управления.  
  
    ```c#  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     Это задает текст надписи текущее значение «MySetting».  
  
6.  Построение пользовательского элемента управления.  
  
7.  В **обозревателе**, откройте source.extension.vsixmanifest.  
  
8.  В редакторе манифеста **марка** для **сохранить мои параметры начальной страницы**.  
  
     Это задает имя начальной страницы, он будет отображаться в **настроить начальную страницу** список **параметры** диалоговое окно.  
  
9. Построение StartPage.xaml.  
  
## <a name="testing-the-control"></a>Тестирование элемента управления  
  
#### <a name="to-test-the-user-control"></a>Чтобы протестировать пользовательский элемент управления  
  
1.  Нажмите клавишу F5.  
  
     Откроется экспериментальный экземпляр Visual Studio.  
  
2.  В экспериментальном экземпляре на **средства** меню, щелкните **параметры**.  
  
3.  В **среды** узел, щелкните **запуска**, а затем в **настроить начальную страницу** выберите **[установленных расширений] сохранить мои параметры начальной страницы**.  
  
     Нажмите кнопку **ОК**.  
  
4.  Закройте начальной страницы, если она открыта, а затем на **представление** меню, щелкните **начальной страницы**.  
  
5.  На начальной странице нажмите кнопку **MyControl** вкладки.  
  
6.  В текстовом поле введите **кошка**, а затем нажмите кнопку **сохранить Мои параметр**.  
  
7.  Закройте начальной страницы и откройте его снова.  
  
     Слова «Cat» должны отображаться в текстовом поле.  
  
8.  Слова «Cat» замените слово «Dog». Не нажимайте кнопку.  
  
9. Закройте начальной страницы и откройте его снова.  
  
     Слово «Dog» должен отображаться в текстовом поле, несмотря на то, что параметр не был сохранен. Это происходит, поскольку Visual Studio сохраняет окна инструментов в памяти, даже если они были закрыты, вплоть до самой Visual Studio.  
  
10. Закройте экспериментальный экземпляр Visual Studio.  
  
11. Нажмите клавишу F5, чтобы снова открыть экспериментальный экземпляр.  
  
12. Слова «Cat» должны отображаться в текстовом поле.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 Вы можете изменить этот пользовательский элемент управления для сохранения и извлечения любое количество пользовательских параметров с помощью различных значений из разных обработчика событий для получения и установки `SettingsStore` свойство. При условии, что можно использовать другой `propertyName` параметра для каждого вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, значения не перезаписывают друг с другом в реестре.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>  
  
## <a name="see-also"></a>См. также  
 <xref:EnvDTE80.DTE2?displayProperty=fullName></xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [Добавление команд Visual Studio на начальной странице](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
