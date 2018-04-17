---
title: 'Пошаговое руководство: Создание пакета SDK с помощью C++ | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33880dc3b9c359798c47c666debc3d5564524794
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Пошаговое руководство: Создание пакета SDK с помощью C++
В этом пошаговом руководстве демонстрируется создание собственной математические библиотеки C++ SDK, пакет SDK как Visual Studio Extension (VSIX) и затем использовать его для создания приложения. Пошаговое руководство состоит из следующие действия:  
  
-   [Для создания собственного и библиотеки среды выполнения Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Создание проекта расширения NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Создание примера приложения, использующего библиотеку классов](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Для создания собственного и библиотеки среды выполнения Windows  
  
1.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2.  В списке шаблонов разверните **Visual C++**, **универсальное приложение для Windows**, а затем выберите **DLL (универсальных приложений Windows)** шаблона. В **имя** укажите `NativeMath`, а затем выберите **ОК** кнопки.  
  
3.  Обновите NativeMath.h, чтобы совпадал со следующим кодом.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Обновление NativeMath.cpp для сопоставления этого кода:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  В **обозревателе решений**, откройте контекстное меню для **решения «NativeMath»**и нажмите кнопку **добавить**, **новый проект**.  
  
6.  В списке шаблонов разверните **Visual C++**, а затем выберите **компонент среды выполнения Windows** шаблона. В **имя** укажите `NativeMathWRT`, а затем выберите **ОК** кнопки.  
  
7.  Обновление Class1.h для сопоставления этого кода:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Обновление Class1.cpp для сопоставления этого кода:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. В строке меню последовательно выберите **Сборка**и **Собрать решение**.  
  
##  <a name="createVSIX"></a> Создание проекта расширения NativeMathVSIX  
  
1.  В **обозревателе решений**, откройте контекстное меню для **решения «NativeMath»**и нажмите кнопку **добавить**, **новый проект**.  
  
2.  В списке шаблонов разверните **Visual C#**, **расширяемости**, а затем выберите **проект VSIX**. В **имя** укажите **NativeMathVSIX**, а затем выберите **ОК** кнопки.
  
3.  В **обозревателе решений**, откройте контекстное меню для **source.extension.vsixmanifest**, а затем выберите **Просмотр кода**.  
  
4.  Используйте следующий XML-код для замены существующих XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  В **обозревателе решений**, откройте контекстное меню для **NativeMathVSIX** проекта, а затем выберите **добавить**, **новый элемент**.  
  
6.  В списке **элементы Visual C#**, разверните **данные**, а затем выберите **XML-файл**. В **имя** укажите `SDKManifest.xml`, а затем выберите **ОК** кнопки.  
  
7.  Замените содержимое файла, используйте этот XML-код:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. В **обозревателе решений**в **NativeMathVSIX** проект, создайте следующую структуру папок:  
  
    ```  
  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
9. В **обозревателе решений**, откройте контекстное меню для **решения «NativeMath»**, а затем выберите **открыть папку в проводнике**.  
  
10. В **проводника**, скопируйте $SolutionRoot$\NativeMath\NativeMath.h, а затем в **обозреватель решений**в **NativeMathVSIX** проекта, вставьте его в $SolutionRoot$ \ Папка NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\.  
  
     Скопируйте $SolutionRoot$\Debug\NativeMath\NativeMath.lib и вставьте его в папке \NativeMathVSIX\DesignTime\Debug\x86\ $SolutionRoot$.  
  
     $SolutionRoot$\Debug\NativeMath\NativeMath.dll скопируйте и вставьте его в папке \NativeMathVSIX\Redist\Debug\x86\ $SolutionRoot$.  
  
     $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll скопируйте и вставьте его в папке \NativeMathVSIX\Redist\Debug\x86 $SolutionRoot$.  
  
     $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd скопируйте и вставьте его в папке \NativeMathVSIX\References\CommonConfiguration\Neutral $SolutionRoot$.  
  
     $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri скопируйте и вставьте его в папке \NativeMathVSIX\References\CommonConfiguration\Neutral $SolutionRoot$.  
  
11. В папке \NativeMathVSIX\DesignTime\Debug\x86\ $SolutionRoot$ создайте текстовый файл с именем NativeMathSDK.props и вставьте в него следующее содержимое:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. В строке меню выберите **представление**, **другие окна**, **окно свойств** (Клавиатура: нажмите клавишу F4).  
  
13. В **обозревателе решений**выберите **NativeMathWRT.winmd** файла. В **свойства** измените **действие при построении** свойства **содержимого**, а затем измените **включить в VSIX** свойства  **Значение true,**.  
  
     Повторите эту процедуру для **NativeMath.h** файла.  
  
     Повторите эту процедуру для **NativeMathWRT.pri** файла.  
  
     Повторите эту процедуру для **NativeMath.Lib** файла.  
  
     Повторите эту процедуру для **NativeMathSDK.props** файла.  
  
14. В **обозревателе решений**выберите **NativeMath.h** файла. В **свойства** измените **включить в VSIX** свойства **True**.  
  
     Повторите эту процедуру для **NativeMath.dll** файла.  
  
     Повторите эту процедуру для **NativeMathWRT.dll** файла.  
  
     Повторите эту процедуру для **SDKManifest.xml** файла.  
  
15. В строке меню последовательно выберите **Сборка**и **Собрать решение**.  
  
16. В **обозревателе решений**, откройте контекстное меню для **NativeMathVSIX** проекта, а затем выберите **открыть папку в проводнике**.  
  
17. В **проводнике**, перейдите в папку $SolutionRoot$ \NativeMathVSIX\bin\Debug\, а затем запустите NativeMathVSIX.vsix, чтобы начать установку.  
  
18. Выберите **установить** кнопку и дождитесь завершения установки запустите Visual Studio.  
  
##  <a name="createSample"></a> Создание примера приложения, использующего библиотеку классов  
  
1.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2.  В списке шаблонов разверните **Visual C++**, **Windows Universal**, а затем выберите **пустое приложение**. В **имя** укажите **NativeMathSDKSample**, а затем выберите **ОК** кнопки.  
  
3.  В **обозревателе решений**, откройте контекстное меню для **NativeMathSDKSample** проекта, а затем выберите **добавить**, **ссылка**.  
  
4.  В **добавить ссылку** разверните диалоговое окно «», в список ссылочных типов, **универсальных приложений Windows**и выберите **расширения**. Наконец, выберите **собственного пакета SDK математические** флажок и нажмите кнопку **ОК** кнопки.
  
5.  Откройте окно свойств проекта для NativeMathSDKSample.  
  
     Свойства, определенные в NativeMathSDK.props были применены при добавлении ссылки. Это можно проверить с помощью проверки **каталоги VC ++** свойства в проекте **свойства конфигурации**.  
  
6.  В **обозревателе решений**файл MainPage.XAML и выполните следующий код XAML, чтобы заменить его содержимое:  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7.  Обновление Mainpage.xaml.h для сопоставления этого кода:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. Обновление MainPage.xaml.cpp для сопоставления этого кода:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. Нажмите клавишу F5, чтобы запустить приложение.  
  
10. В приложении, ввести любых двух чисел, выберите операцию и выберите **=** кнопки.  
  
     Отображается правильный результат.  
  
 В этом пошаговом руководстве показано, как создать и использовать пакет SDK расширения для вызова [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] библиотеки и значение, отличное от[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] библиотеки.  
  
## <a name="next-steps"></a>Следующие шаги  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Создание пакета SDK с помощью C# или Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Создание пакета средств разработки для программного обеспечения](../extensibility/creating-a-software-development-kit.md)