---
title: 'Пошаговое руководство: Создание пакета SDK с помощью C# или Visual Basic | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf5d738751a4873858aaa1ad80179663d9a7b767
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495951"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Пошаговое руководство: Создание пакета SDK, с помощью C# или Visual Basic
В этом пошаговом руководстве вы узнаете, как создать простой пакет SDK для математической библиотеки с помощью Visual C# и затем пакета SDK в Visual Studio Extension (VSIX). Вы выполните следующие процедуры:  
  
-   [Для создания компонента среды выполнения Windows SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [Создание проекта расширения SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
-   [Чтобы создать приложение-пример, использующий библиотеку классов](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Для создания компонента среды выполнения Windows SimpleMath  
  
1.  В строке меню выберите **файл** > **New** > **новый проект**.  
  
2.  В списке шаблонов разверните **Visual C#** или **Visual Basic**, выберите **Windows Store** узел, а затем выберите **компонента среды выполнения Windows** шаблона.  
  
3.  В **имя** укажите **SimpleMath**, а затем выберите **ОК** кнопки.  
  
4.  В **обозревателе решений**, откройте контекстное меню для **SimpleMath** узел проекта, а затем выберите **свойства**.  
  
5.  Переименуйте **Class1.cs** для **Arithmetic.cs** и измените его в следующем коде:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]  
  
6.  В **обозревателе решений**, откройте контекстное меню для **решение «SimpleMath»** узел, а затем выберите **Configuration Manager**.  
  
     **Configuration Manager** откроется диалоговое окно.  
  
7.  В **активная конфигурация решения** выберите **выпуска**.  
  
8.  В **конфигурации** столбец, убедитесь, что **SimpleMath** строки равен **выпуска**, а затем выберите **закрыть** кнопку, чтобы принять изменение.  
  
    > [!IMPORTANT]
    >  Пакет SDK для компонента SimpleMath включает только одну конфигурацию. Этой конфигурации должен содержать сборку выпуска, или приложения, использующие компонент не будет передавать сертификации[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].  
  
9. В **обозревателе решений**, откройте контекстное меню для **SimpleMath** узел проекта, а затем выберите **построения**.  
  
##  <a name="createVSIX"></a> Создание проекта расширения SimpleMathVSIX  
  
1.  В контекстном меню для **решение «SimpleMath»** узел, выберите **добавить** > **новый проект**.  
  
2.  В списке шаблонов разверните **Visual C#** или **Visual Basic**, выберите **расширяемости** узел, а затем выберите **проект VSIX** шаблон.  
  
3.  В **имя** укажите **SimpleMathVSIX**, а затем выберите **ОК** кнопки.  
  
4.  В **обозревателе решений**, выберите **source.extension.vsixmanifest** элемента.  
  
5.  В строке меню выберите **Вид** > **Код**.  
  
6.  Замените существующий XML-код следующим кодом XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  В **обозревателе решений**, выберите **SimpleMathVSIX** проекта.  
  
8.  В строке меню выберите **Проект** > **Добавить новый элемент**.  
  
9. В списке **общих элементов**, разверните **данных**, а затем выберите **XML-файл**.  
  
10. В **имя** укажите `SDKManifest.xml`, а затем выберите **добавить** кнопки.  
  
11. В **обозревателе решений**, откройте контекстное меню для `SDKManifest.xml`, выберите **свойства**, а затем измените значение **включить в VSIX** свойства **True**.  
  
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
  
13. В **обозревателе решений**, откройте контекстное меню для **SimpleMathVSIX** проекта, выберите **добавить**, а затем выберите **новую папку**.  
  
14. Переименуйте папку в `references`.  
  
15. Откройте контекстное меню для **ссылки** папку, выберите **добавить**, а затем выберите **новую папку**.  
  
16. Переименуйте вложенную папку для `commonconfiguration`, создайте вложенную папку внутри нее и именем `neutral`.  
  
17. Повторите предыдущие четыре шага, в настоящее время переименования первой папки для `redist`.  
  
     Теперь проект содержит следующую структуру папок:  
  
    ```xml
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. В **обозревателе решений**, откройте контекстное меню для **SimpleMath** проекта, а затем выберите **открыть папку в проводнике**.  
  
19. В **проводнике**, перейдите к *bin\Release* папку, откройте контекстное меню для **SimpleMath.winmd** файл, а затем выберите **скопируйте**.  
  
20. В **обозревателе решений**, вставьте файл в *references\commonconfiguration\neutral* папку в **SimpleMathVSIX** проекта.  
  
21. Повторите предыдущий шаг, вставив **SimpleMath.pri** файл в *redist\commonconfiguration\neutral* папку в **SimpleMathVSIX** проекта.  
  
22. В **обозревателе решений**, выберите **SimpleMath.winmd**.  
  
23. В строке меню выберите **представление** > **свойства** (клавиатуры: выберите **F4** ключ).  
  
24. В **свойства** измените **действие при построении** свойства **содержимого**, а затем измените **включить в VSIX** свойства  **Значение true,**.  
  
25. В **обозревателе решений**, повторите эту процедуру для **SimpleMath.pri**.  
  
26. В **обозревателе решений**, выберите **SimpleMathVSIX** проекта.  
  
27. В строке меню выберите **построения** > **построения SimpleMathVSIX**.  
  
28. В **обозревателе решений**, откройте контекстное меню для **SimpleMathVSIX** проекта, а затем выберите **открыть папку в проводнике**.  
  
29. В **проводнике**, перейдите к *\bin\Release* папку, а затем выполните *SimpleMathVSIX.vsix* установить его.  
  
30. Выберите **установить** кнопку и дождитесь завершения установки перезапустите Visual Studio.  
  
##  <a name="createSample"></a> Чтобы создать приложение-пример, использующий библиотеку классов  
  
1.  В строке меню выберите **файл** > **New** > **новый проект**.  
  
2.  В списке шаблонов разверните **Visual C#** или **Visual Basic**, а затем выберите **Windows Store** узла.  
  
3.  Выберите **пустое приложение** шаблон, имя проекта **ArithmeticUI**, а затем выберите **ОК** кнопки.  
  
4.  В **обозревателе решений**, откройте контекстное меню для **ArithmeticUI** проекта, а затем выберите **добавить** > **ссылку**.  
  
5.  В списке ссылочных типов, разверните **Windows**, а затем выберите **расширения**.  
  
6.  В области сведений выберите **пакета SDK для простой математической** расширения.  
  
     Отображение дополнительных сведений о вашем пакете SDK. Вы можете выбрать **Подробнее** ссылку, чтобы открыть https://msdn.microsoft.com/, как указано в файле SDKManifest.xml ранее в этом пошаговом руководстве.  
  
7.  В **диспетчер ссылок** выберите **пакета SDK для простой математической** , а затем нажать **ОК** кнопки.  
  
8.  В строке меню выберите **представление** > **обозреватель объектов**.  
  
9. В **Обзор** выберите **простых математических расчетов**.  
  
     Теперь вы можете изучить возможности пакета SDK.  
  
10. В **обозревателе решений**откройте **MainPage.xaml**и замените его содержимое на следующий XAML:  

    **C#**
    ```xml
    <Page
        x:Class="WinRTMathTestCS.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTestCS"
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
        x:Class="WinRTMathTest.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTest"
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
  
11. Обновление **MainPage.xaml.cs** в соответствии с следующий код:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]  
  
12. Выберите **F5** клавишу, чтобы запустить приложение.  
  
13. В приложении введите любых двух чисел, выберите операцию и затем выберите **=** кнопки.  
  
     Отображается правильный результат.  
  
 Вы успешно создали и использовать пакет SDK расширения.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Создание пакета SDK, с помощью C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Пошаговое руководство: Создание пакета SDK, с помощью JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)   
 [Создание пакета средств разработки программного обеспечения](../extensibility/creating-a-software-development-kit.md)