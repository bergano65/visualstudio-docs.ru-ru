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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202073"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Пошаговое руководство. Создание пакета SDK с помощью C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как создать собственный пакет SDK для математической библиотеки C++, упаковать пакет SDK как расширение Visual Studio (VSIX) и использовать его для создания приложения. Пошаговое руководство делится на следующие этапы.  
  
- [Создание собственных и среда выполнения Windows библиотек](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [Создание проекта расширения Нативемасвсикс](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [Создание примера приложения, использующего библиотеку классов](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> Создание собственных и среда выполнения Windows библиотек  
  
1. В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2. В списке шаблонов разверните узел **Visual C++**, **Магазин Windows**, а затем выберите шаблон **DLL (приложения для Магазина Windows)** . В поле **имя** укажите `NativeMath` , а затем нажмите кнопку **ОК** .  
  
3. Обновите Нативемас. h в соответствии с приведенным ниже кодом.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. Обновите Нативемас. cpp в соответствии с этим кодом:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. В **Обозреватель решений**откройте контекстное меню для **решения "нативемас"**, а затем выберите **добавить**, **Новый проект**.  
  
6. В списке шаблонов разверните узел **Visual C++**, а затем выберите шаблон **компонента Среда выполнения Windows** . В поле **имя** укажите `NativeMathWRT` , а затем нажмите кнопку **ОК** .  
  
7. Обновите Class1. h, чтобы он соответствовал этому коду:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. Обновите Class1. cpp, чтобы он соответствовал этому коду:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. В строке меню последовательно выберите **Сборка**и **Собрать решение**.  
  
## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Создание проекта расширения Нативемасвсикс  
  
1. В **Обозреватель решений**откройте контекстное меню для **решения "нативемас"**, а затем выберите **добавить**, **Новый проект**.  
  
2. В списке шаблонов разверните узел **Visual C#**, **расширяемость**, а затем выберите **пакет VSIX**. В поле **имя** укажите **нативемасвсикс**, а затем нажмите кнопку **ОК** .  
  
3. Когда откроется конструктор манифеста VSIX, закройте его.  
  
4. В **Обозреватель решений**откройте контекстное меню **source. extension. vsixmanifest**и выберите пункт **Просмотреть код**.  
  
5. Используйте следующий XML-код, чтобы заменить существующий XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. В **Обозреватель решений**откройте контекстное меню проекта **нативемасвсикс** , а затем выберите **добавить**, **новый элемент**.  
  
7. В списке **элементов Visual C#** разверните узел **данные**, а затем выберите пункт **XML-файл**. В поле **имя** укажите `SDKManifest.xml` , а затем нажмите кнопку **ОК** .  
  
8. Используйте этот XML-код для замены содержимого файла:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. В **Обозреватель решений**в проекте **нативемасвсикс** создайте следующую структуру папок:  
  
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
  
10. В **Обозреватель решений**откройте контекстное меню **решения "нативемас"**, а затем выберите пункт **Открыть папку в проводнике**.  
  
11. В **проводнике скопируйте файл**\нативемас\нативемас.х, а затем в **Обозреватель решений**в проекте **нативемасвсикс** вставьте его в папку \десигнтиме\коммонконфигуратион\неутрал\инклуде\.  
  
     Скопируйте \Дебуг\нативемас\нативемас.либ и вставьте его в папку \DesignTime\Debug\x86\.  
  
     Скопируйте \Debug\NativeMath\NativeMath.dll и вставьте его в папку \Redist\Debug\x86\  
  
     Скопируйте DebugNativeMathWRTNativeMathWRT.dll и вставьте его в папку RedistDebugx86  
  
     Скопируйте Дебугнативемасвртнативемасврт. winmd и вставьте его в папку Референцескоммонконфигуратионнеутрал.  
  
     Скопируйте Дебугнативемасвртнативемасврт. PRI и вставьте его в папку Референцескоммонконфигуратионнеутрал.  
  
12. В папке \DesignTime\Debug\x86\ создайте текстовый файл с именем Нативемассдк. props, а затем вставьте в него следующее содержимое:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. В строке меню выберите **вид**, **другие окна**, **окно свойств** (клавиатура: нажмите клавишу F4).  
  
14. В **Обозреватель решений**выберите файл **нативемасврт. winmd** . В окне **Свойства** измените свойство **действие сборки** на **содержимое**, а затем измените значение свойства **включить в VSIX** на **true**.  
  
     Повторите эту процедуру для файла **симплемас. PRI** .  
  
     Повторите эту процедуру для файла **нативемас. lib** .  
  
     Повторите эту процедуру для файла **нативемассдк. props** .  
  
15. В **Обозреватель решений**выберите файл **нативемас. h** . В окне **Свойства** измените значение свойства **включить в VSIX** на **true**.  
  
     Повторите эту процедуру для файла **NativeMath.dll** .  
  
     Повторите эту процедуру для файла **NativeMathWRT.dll** .  
  
     Повторите эту процедуру для файла **SDKManifest.xml** .  
  
16. В строке меню последовательно выберите **Сборка**и **Собрать решение**.  
  
17. В **Обозреватель решений**откройте контекстное меню проекта **нативемасвсикс** , а затем выберите пункт **Открыть папку в проводнике**.  
  
18. В **проводнике**перейдите в папку \bin\Debug\, а затем запустите нативемасвсикс. VSIX, чтобы начать установку.  
  
19. Нажмите кнопку **установить** , дождитесь завершения установки, а затем перезапустите Visual Studio.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Создание примера приложения, использующего библиотеку классов  
  
1. В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2. В списке шаблонов разверните узел **Visual C++**, **Магазин Windows**, а затем выберите **пустое приложение**. В поле **имя** укажите **нативемассдксампле**, а затем нажмите кнопку **ОК** .  
  
3. В **Обозреватель решений**откройте контекстное меню проекта **Нативемассдксампле** и выберите **добавить**, **ссылка**.  
  
4. На странице свойств **Общие свойства**, **платформа и ссылки** в списке ссылочных типов разверните узел **Windows**, а затем выберите **расширения**. В области сведений выберите расширение **встроенного пакета SDK для математических** функций, а затем нажмите кнопку **Добавить новую ссылку** .  
  
5. В диалоговом окне **Добавление ссылки** установите флажок **собственный математический пакет SDK** , а затем нажмите кнопку **ОК** .  
  
6. Отображение свойств проекта для Нативемассдксампле.  
  
    Свойства, определенные в Нативемассдк. props, были применены при добавлении ссылки. Это можно проверить, изучив свойство " **каталоги VC + +** " **свойств конфигурации**проекта.  
  
7. В **Обозреватель решений**Откройте MainPage. XAML, а затем используйте следующий XAML для замены его содержимого:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Обновите MainPage. XAML. h, чтобы сопоставить этот код:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. Обновите MainPage. XAML. cpp, чтобы сопоставить этот код:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Нажмите клавишу F5, чтобы запустить приложение.  
  
11. В приложении введите любые два числа, выберите операцию, а затем нажмите **=** кнопку.  
  
     Появится правильный результат.  
  
    В этом пошаговом руководстве показано, как создать и использовать пакет SDK расширения для вызова [!INCLUDE[wrt](../includes/wrt-md.md)] библиотеки и не [!INCLUDE[wrt](../includes/wrt-md.md)] библиотеки.  
  
## <a name="next-steps"></a>Next Steps  
  
## <a name="see-also"></a>См. также:  
 [Пошаговое руководство. Создание пакета SDK на C# или Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Создание пакета средств разработки для программного обеспечения](../extensibility/creating-a-software-development-kit.md)
