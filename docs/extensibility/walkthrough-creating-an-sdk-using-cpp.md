---
title: Пошаговое руководство. Создание пакета SDK с помощью C++ | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2a0db4f34315f9e0eb4a5627cdc286a43a904a34
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917609"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Пошаговое руководство. Создайте пакет SDK, с помощью C++
В этом пошаговом руководстве показано, как создать собственной математические библиотеки C++ SDK, пакет SDK в Visual Studio Extension (VSIX) и затем использовать его для создания приложения. Пошаговое руководство содержит следующие действия.  
  
-   [Чтобы создать машинный код и библиотеки среды выполнения Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Создание проекта расширения NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Чтобы создать приложение-пример, использующий библиотеку классов](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Чтобы создать машинный код и библиотеки среды выполнения Windows  
  
1.  В строке меню выберите **Файл** > **Создать** > **Проект**.  
  
2.  В списке шаблонов разверните **Visual C++** > **универсальной Windows**, а затем выберите **DLL (приложения для универсальной Windows)** шаблона. В **имя** укажите `NativeMath`, а затем выберите **ОК** кнопки.  
  
3.  Обновление *NativeMath.h* в соответствии с следующий код.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Обновление *NativeMath.cpp* в соответствии с этот код:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  В **обозревателе решений**, откройте контекстное меню для **решение «NativeMath»**, а затем выберите **добавить** > **новый проект**.  
  
6.  В списке шаблонов разверните **Visual C++**, а затем выберите **компонента среды выполнения Windows** шаблона. В **имя** укажите `NativeMathWRT`, а затем выберите **ОК** кнопки.  
  
7.  Обновление *Class1.h* в соответствии с этот код:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Обновление *Class1.cpp* в соответствии с этот код:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. В строке меню последовательно выберите **Сборка**  >  **Собрать решение**.  
  
##  <a name="createVSIX"></a> Создание проекта расширения NativeMathVSIX  
  
1.  В **обозревателе решений**, откройте контекстное меню для **решение «NativeMath»**, а затем выберите **добавить** > **новый проект**.  
  
2.  В списке шаблонов разверните **Visual C#** > **расширяемости**, а затем выберите **проект VSIX**. В **имя** укажите **NativeMathVSIX**, а затем выберите **ОК** кнопки.
  
3.  В **обозревателе решений**, откройте контекстное меню для **source.extension.vsixmanifest**, а затем выберите **Просмотр кода**.  
  
4.  Используйте следующий код XML для замены существующих XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  В **обозревателе решений**, откройте контекстное меню для **NativeMathVSIX** проекта, а затем выберите **добавить** > **новый элемент**.  
  
6.  В списке **элементы Visual C#**, разверните **данных**, а затем выберите **XML-файл**. В **имя** укажите `SDKManifest.xml`, а затем выберите **ОК** кнопки.  
  
7.  Используйте этот код XML, замените содержимое файла:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. В **обозревателе решений**в разделе **NativeMathVSIX** проект, создайте эту структуру папок:  
  
    ```xml  
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
  
9. В **обозревателе решений**, откройте контекстное меню для **решение «NativeMath»**, а затем выберите **открыть папку в проводнике**.  
  
10. В **проводнике**, копирования *$SolutionRoot$\NativeMath\NativeMath.h*, а затем в **обозревателе решений**в разделе **NativeMathVSIX**проекта и вставьте его в *$SolutionRoot$ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\\*  папки.  
  
     Копировать *$SolutionRoot$\Debug\NativeMath\NativeMath.lib*, а затем вставьте его в *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  папки.  
  
     Копировать *$SolutionRoot$\Debug\NativeMath\NativeMath.dll* и вставьте его в *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86\\*  папки.  
  
     Копировать *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* и вставьте его в *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86* папки.  
     Копировать *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* и вставьте его в *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* папки.  
  
     Копировать *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* и вставьте его в *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* папки.  
  
11. В *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  папке создайте текстовый файл с именем *NativeMathSDK.props*и вставьте в него следующее содержимое:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. В строке меню выберите **представление** > **Other Windows** > **окно "Свойства"** (клавиатуры: Выберите **F4** ключ).  
  
13. В **обозревателе решений**выберите **NativeMathWRT.winmd** файла. В **свойства** измените **действие при построении** свойства **содержимого**, а затем измените **включить в VSIX** свойства  **Значение true,**.  
  
     Повторите эту процедуру для **NativeMath.h** файла.  
  
     Повторите эту процедуру для **NativeMathWRT.pri** файла.  
  
     Повторите эту процедуру для **NativeMath.Lib** файла.  
  
     Повторите эту процедуру для **NativeMathSDK.props** файла.  
  
14. В **обозревателе решений**выберите **NativeMath.h** файла. В **свойства** измените **включить в VSIX** свойства **True**.  
  
     Повторите эту процедуру для **NativeMath.dll** файла.  
  
     Повторите эту процедуру для **NativeMathWRT.dll** файла.  
  
     Повторите эту процедуру для **SDKManifest.xml** файла.  
  
15. В строке меню последовательно выберите **Сборка**  >  **Собрать решение**.  
  
16. В **обозревателе решений**, откройте контекстное меню для **NativeMathVSIX** проекта, а затем выберите **открыть папку в проводнике**.  
  
17. В **проводнике**, перейдите к *$SolutionRoot$ \NativeMathVSIX\bin\Debug* папку, а затем выполните *NativeMathVSIX.vsix* чтобы начать установку.  
  
18. Выберите **установить** кнопку, дождитесь завершения процесса установки и затем запустите Visual Studio.  
  
##  <a name="createSample"></a> Чтобы создать приложение-пример, использующий библиотеку классов  
  
1. В строке меню выберите **Файл** > **Создать** > **Проект**.  
  
2. В списке шаблонов разверните **Visual C++** > **универсальной Windows** , а затем выберите **пустое приложение**. В **имя** укажите **NativeMathSDKSample**, а затем выберите **ОК** кнопки.  
  
3. В **обозревателе решений**, откройте контекстное меню для **NativeMathSDKSample** проекта, а затем выберите **добавить** > **ссылку**.  
  
4. В **добавить ссылку** разверните диалоговое окно, в список ссылочных типов, **универсальной Windows**, а затем выберите **расширения**. Наконец, выберите **собственным пакетом SDK для математических** , а затем нажать **ОК** кнопки.
  
5. Отображение свойств проекта для NativeMathSDKSample.  
  
    Свойства, определенные в *NativeMathSDK.props* были применены при добавлении ссылки. Можно проверить свойства были применены с помощью проверки **каталоги VC ++** свойства в проекте **свойства конфигурации**.  
  
6. В **обозревателе решений**откройте **MainPage.xaml**, а затем замените его содержимое с помощью следующих XAML:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7. Обновление *Mainpage.xaml.h* в соответствии с этот код:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. Обновление *MainPage.xaml.cpp* в соответствии с этот код:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. Выберите **F5** клавишу, чтобы запустить приложение.  
  
10. В приложении введите любых двух чисел, выберите операцию, а затем нажмите **=** кнопки.  
  
     Отображается правильный результат.  
  
    В этом пошаговом руководстве было показано, как создать и использовать пакет SDK расширения для вызова [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] библиотеки и отличным от[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] библиотеки.  
  
## <a name="next-steps"></a>Следующие шаги  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Создание пакета SDK с помощью C# или Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Создание пакета средств разработки программного обеспечения](../extensibility/creating-a-software-development-kit.md)
