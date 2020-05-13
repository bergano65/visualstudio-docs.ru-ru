---
title: 'Пошаговая прогулка: Создание SDK с использованием C или Visual Basic Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16eb20452601a65c498ff112ea996f2d93559940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697556"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Прохождение: Создание SDK с использованием C или Visual Basic
В этом пошаговом шаге вы узнаете, как создать простую Матетическую библиотеку SDK с помощью Visual C, а затем упаковать SDK в качестве расширения визуальной студии (VSIX). Вы завершите следующие процедуры:

- [Создание компонента SimpleMath Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [Создание проекта расширения SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Для создания примера приложения, используюшего библиотеку классов](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации, [см.](../extensibility/visual-studio-sdk.md)

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>Создание компонента SimpleMath Windows Runtime

1. В меню-баре выберите **File** > **New** > **Project.**

2. В списке шаблонов расширьте **Visual C или** Visual **Basic,** выберите узло **магазина Windows,** а затем выберите шаблон **компонента Runtime Windows.**

3. В поле **Name** укажите **SimpleMath,** а затем выберите кнопку **OK.**

4. В **Solution Explorer**откройте меню ярлыка для узла проекта **SimpleMath,** а затем выберите **Свойства.**

5. Переименуйте **Class1.cs,** чтобы **Arithmetic.cs** и обновить его в соответствии со следующим кодом:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. В **Solution Explorer**откройте меню ярлыка для узла решения **'SimpleMath',** а затем выберите **диспетчер конфигурации.**

    Открывается диалоговая коробка **configuration Manager.**

7. В списке **конфигураций активных решений** выберите **Release**.

8. В столбце **Конфигурации** убедитесь, что строка **SimpleMath** настроена на **выпуск,** а затем выберите кнопку **«Закрыть»** для принятия изменения.

   > [!IMPORTANT]
   > SDK для компонента SimpleMath включает только одну конфигурацию. Эта конфигурация должна быть сборкой релиза, или приложения, [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]которые используют компонент, не пройдут сертификацию для .

9. В **Solution Explorer**откройте меню ярлыка для узла проекта **SimpleMath,** а затем выберите **Build.**

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a>Создание проекта расширения SimpleMathVSIX

1. В меню ярлыка для узла **решения 'SimpleMath)** выберите **Добавить** > **новый проект.**

2. В списке шаблонов расширьте **Visual C или** Visual **Basic,** выберите узло **расширения,** а затем выберите шаблон **проекта VSIX.**

3. В поле **Name** укажите **SimpleMathVSIX,** а затем выберите кнопку **OK.**

4. В **Solution Explorer**выберите элемент **source.extension.vsixmanifest.**

5. В меню-баре выберите **View** > **Code**.

6. Замените существующий XML на следующий XML:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. В **Solution Explorer**выберите проект **SimpleMathVSIX.**

8. В панели меню выберите **Project** > **Add New Item.**

9. В списке **общих элементов**, расширить **данные**, а затем выбрать **XML файл**.

10. В поле **Имя,** укажите, `SDKManifest.xml`а затем выбрать кнопку **Добавить.**

11. В **Solution Explorer**откройте меню `SDKManifest.xml`ярлыка для, выберите **Свойства,** а затем измените значение Включения в свойство **VSIX** на **True.**

12. Замените содержимое файла следующим XML-кодом.

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. В **Solution Explorer**откройте меню ярлыка для проекта **SimpleMathVSIX,** выберите **Добавить,** а затем выберите **New Folder.**

14. Переименуем папку в `references`.

15. Откройте меню ярлыка для **папки Ссылки,** выберите **Добавить,** а затем выберите **New Folder.**

16. Переименуйте `commonconfiguration`субфолдер, создайте субфолдер в нем и `neutral`назовите субфолдер.

17. Повторите предыдущие четыре шага, на этот раз `redist`переименовав первую папку в .

     Теперь проект содержит следующую структуру папок:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. В **Solution Explorer**откройте меню ярлыка для проекта **SimpleMath,** а затем выберите Open **Folder в File Explorer.**

19. В **файле Explorer**, перейдите к папке *бин-релиз,* откройте меню ярлыка для файла **SimpleMath.winmd,** а затем выберите **Copy**.

20. В **Solution Explorer**вставьте файл в *папку с ссылками в* рамках проекта **SimpleMathVSIX.**

21. Повторите предыдущий шаг, вставив файл **SimpleMath.pri** в *редистно-обычную* папку в проекте **SimpleMathVSIX.**

22. В **Solution Explorer**выберите **SimpleMath.winmd**.

23. В баре меню выберите **View** > **Properties** (клавиатура: Выберите ключ **F4).**

24. В окне **Свойств** измените свойство **Build Action** на **содержимое,** а затем измените **свойство «Включить» в свойство VSIX** на **True.**

25. В **Solution Explorer**повторите этот процесс для **SimpleMath.pri**.

26. В **Solution Explorer**выберите проект **SimpleMathVSIX.**

27. В меню-баре выберите **Build** > **SimpleMathVSIX.**

28. В **Solution Explorer**откройте меню ярлыка для проекта **SimpleMathVSIX,** а затем выберите **Open Folder в File Explorer.**

29. В **Файл Explorer**, перейдите к папке *«Бин-Release»,* а затем запустите *SimpleMathVSIX.vsix,* чтобы установить ее.

30. Выберите кнопку **«Установка»,** подождите, пока установка закончится, а затем перезапустите Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Для создания примера приложения, используюшего библиотеку классов

1. В меню-баре выберите **File** > **New** > **Project.**

2. В списке шаблонов расширьте **Visual C или** Visual **Basic,** а затем выберите узло **магазина Windows.**

3. Выберите шаблон **Blank App,** назовите проект **ArithmeticUI,** а затем выберите кнопку **OK.**

4. В **Solution Explorer**откройте меню ярлыка для проекта **ArithmeticUI,** а затем выберите **Добавить** > **справку.**

5. В списке типов ссылок расширьте **Windows,** а затем выберите **расширения.**

6. В деталях панели, выберите **расширение библиотеки математики WinRT.**

    Появляется дополнительная информация о вашем SDK. Вы можете выбрать **ссылку на более подробную информацию,** чтобы открыть, https://msdn.microsoft.com/как вы указано в файле SDKManifest.xml ранее в этом пошаговом шаге.

7. В диалоговом окне **справочника Reference Manager** выберите флажок **библиотеки Математика WinRT,** а затем выберите кнопку **OK.**

8. В строке меню выберите **браузер «Посмотреть** > **объект».**

9. В списке **просмотра** выберите **простую математику.**

     Теперь вы можете исследовать, что в SDK.

10. В **Solution Explorer**, открыть **MainPage.xaml**, и заменить его содержимое со следующими XAML:

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. Обновление **MainPage.xaml.cs** в соответствии со следующим кодом:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Выберите ключ **F5** для запуска приложения.

13. В приложении введите любые два номера, **=** выберите операцию, а затем выберите кнопку.

     Появляется правильный результат.

    Вы успешно создали и использовали Расширение SDK.

## <a name="see-also"></a>См. также
- [Прохождение: Создание SDK с помощью СЗЗ](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Пошаговый шаг: Создание SDK с помощью JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Создание пакета средств разработки](../extensibility/creating-a-software-development-kit.md)
