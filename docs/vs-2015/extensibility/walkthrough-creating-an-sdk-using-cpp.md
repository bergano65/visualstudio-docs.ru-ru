---
title: Пошаговое руководство. Создание пакета SDK с помощью C++ | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1312d61b2d287a5dd8cb757b73e818a9e9cb2241
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202073"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Пошаговое руководство. Создание пакета SDK с помощью C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как создать собственной математические библиотеки C++ SDK, пакет SDK в Visual Studio Extension (VSIX) и затем использовать его для создания приложения. Пошаговое руководство содержит следующие действия.  
  
- [Чтобы создать машинный код и библиотеки среды выполнения Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [Создание проекта расширения NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [Чтобы создать приложение-пример, использующий библиотеку классов](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="createClassLibrary"></a> Чтобы создать машинный код и библиотеки среды выполнения Windows  
  
1. В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2. В списке шаблонов разверните **Visual C++** , **Windows Store**, а затем выберите **DLL (приложения Windows Store)** шаблона. В **имя** укажите `NativeMath`, а затем выберите **ОК** кнопки.  
  
3. Обновите NativeMath.h в соответствии с следующий код.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. Обновите NativeMath.cpp в соответствии с этот код:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. В **обозревателе решений**, откройте контекстное меню для **решение «NativeMath»** , а затем выберите **добавить**, **новый проект**.  
  
6. В списке шаблонов разверните **Visual C++** , а затем выберите **компонента среды выполнения Windows** шаблона. В **имя** укажите `NativeMathWRT`, а затем выберите **ОК** кнопки.  
  
7. Обновите файл Class1.h в соответствии с этот код:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. Обновите Class1.cpp в соответствии с этот код:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. В строке меню последовательно выберите **Сборка**и **Собрать решение**.  
  
## <a name="createVSIX"></a> Создание проекта расширения NativeMathVSIX  
  
1. В **обозревателе решений**, откройте контекстное меню для **решение «NativeMath»** , а затем выберите **добавить**, **новый проект**.  
  
2. В списке шаблонов разверните **Visual C#** , **расширяемости**, а затем выберите **пакет VSIX**. В **имя** укажите **NativeMathVSIX**, а затем выберите **ОК** кнопки.  
  
3. После открытия конструктора манифеста VSIX, закройте его.  
  
4. В **обозревателе решений**, откройте контекстное меню для **source.extension.vsixmanifest**, а затем выберите **Просмотр кода**.  
  
5. Используйте следующий код XML для замены существующих XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. В **обозревателе решений**, откройте контекстное меню для **NativeMathVSIX** проекта, а затем выберите **добавить**, **новый элемент**.  
  
7. В списке **элементы Visual C#** , разверните **данных**, а затем выберите **XML-файл**. В **имя** укажите `SDKManifest.xml`, а затем выберите **ОК** кнопки.  
  
8. Используйте этот код XML, замените содержимое файла:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. В **обозревателе решений**в **NativeMathVSIX** проект, создайте эту структуру папок:  
  
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
  
10. В **обозревателе решений**, откройте контекстное меню для **решение «NativeMath»** , а затем выберите **открыть папку в проводнике**.  
  
11. В **проводнике**, скопируйте \NativeMath\NativeMath.h, а затем в **обозревателе решений**в **NativeMathVSIX** проекта и вставьте его в \DesignTime\ Папка CommonConfiguration\Neutral\Include\.  
  
     Скопируйте \Debug\NativeMath\NativeMath.lib, а затем вставьте его в папке \DesignTime\Debug\x86\.  
  
     Скопируйте \Debug\NativeMath\NativeMath.dll и вставьте его в папке \Redist\Debug\x86\.  
  
     Скопируйте DebugNativeMathWRTNativeMathWRT.dll и вставьте его в папке RedistDebugx86.  
  
     Скопируйте DebugNativeMathWRTNativeMathWRT.winmd и вставьте его в папке ReferencesCommonConfigurationNeutral.  
  
     Скопируйте DebugNativeMathWRTNativeMathWRT.pri и вставьте его в папке ReferencesCommonConfigurationNeutral.  
  
12. В папке \DesignTime\Debug\x86\ создайте текстовый файл с именем NativeMathSDK.props и вставьте в него следующее содержимое:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. В строке меню выберите **представление**, **Other Windows**, **окно "Свойства"** (клавиатуры: Нажмите клавишу F4).  
  
14. В **обозревателе решений**выберите **NativeMathWRT.winmd** файла. В **свойства** измените **действие при построении** свойства **содержимого**, а затем измените **включить в VSIX** свойства  **Значение true,** .  
  
     Повторите эту процедуру для **SimpleMath.pri** файла.  
  
     Повторите эту процедуру для **NativeMath.Lib** файла.  
  
     Повторите эту процедуру для **NativeMathSDK.props** файла.  
  
15. В **обозревателе решений**выберите **NativeMath.h** файла. В **свойства** измените **включить в VSIX** свойства **True**.  
  
     Повторите эту процедуру для **NativeMath.dll** файла.  
  
     Повторите эту процедуру для **NativeMathWRT.dll** файла.  
  
     Повторите эту процедуру для **SDKManifest.xml** файла.  
  
16. В строке меню последовательно выберите **Сборка**и **Собрать решение**.  
  
17. В **обозревателе решений**, откройте контекстное меню для **NativeMathVSIX** проекта, а затем выберите **открыть папку в проводнике**.  
  
18. В **проводнике**, перейдите к папке \bin\Debug\, а затем запустите NativeMathVSIX.vsix, чтобы начать установку.  
  
19. Выберите **установить** кнопку и дождитесь завершения установки перезапустите Visual Studio.  
  
## <a name="createSample"></a> Чтобы создать приложение-пример, использующий библиотеку классов  
  
1. В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2. В списке шаблонов разверните **Visual C++** , **Windows Store**, а затем выберите **пустое приложение**. В **имя** укажите **NativeMathSDKSample**, а затем выберите **ОК** кнопки.  
  
3. В **обозревателе решений**, откройте контекстное меню для **NativeMathSDKSample** проекта, а затем выберите **добавить**, **ссылку**.  
  
4. На **общие свойства**, **.NET Framework и ссылки** странице свойств, в список ссылочных типов, разверните **Windows**, а затем выберите **расширения** . В области сведений выберите **собственным пакетом SDK для математических** расширения, а затем выберите **добавить новую ссылку** кнопки.  
  
5. В **добавить ссылку** выберите **собственным пакетом SDK для математических** , а затем нажать **ОК** кнопки.  
  
6. Отображение свойств проекта для NativeMathSDKSample.  
  
    Свойства, определенные в NativeMathSDK.props были применены при добавлении ссылки. Это можно проверить с помощью проверки **каталоги VC ++** свойства в проекте **свойства конфигурации**.  
  
7. В **обозревателе решений**, откройте файл MainPage.xaml и выполните следующий XAML, чтобы заменить его содержимое:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Обновите Mainpage.xaml.h в соответствии с этот код:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. Обновите MainPage.xaml.cpp в соответствии с этот код:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Нажмите клавишу F5, чтобы запустить приложение.  
  
11. В приложении введите любых двух чисел, выберите операцию, а затем нажмите **=** кнопки.  
  
     Отображается правильный результат.  
  
    В этом пошаговом руководстве было показано, как создать и использовать пакет SDK расширения для вызова [!INCLUDE[wrt](../includes/wrt-md.md)] библиотеки и отличным от[!INCLUDE[wrt](../includes/wrt-md.md)] библиотеки.  
  
## <a name="next-steps"></a>Следующие шаги  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Создание пакета SDK с помощью C# или Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Создание пакета средств разработки для программного обеспечения](../extensibility/creating-a-software-development-kit.md)
