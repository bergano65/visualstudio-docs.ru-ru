---
title: 'Пошаговая прогулка: Создание SDK с использованием СЗЗ Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65643e65490eacb79eea4d76aa49ff10d6cccf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697631"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Прохождение: Создание SDK с помощью СЗЗ
В этом пошаговом показании, как создать родную библиотеку математики SDK, упаковать SDK в качестве расширения визуальной студии (VSIX), а затем использовать его для создания приложения. Пошаговая часть разделена на следующие шаги:

- [Создание родных библиотек и библиотек Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Создание проекта расширения NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Для создания примера приложения, используюшего библиотеку классов](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации, [см.](../extensibility/visual-studio-sdk.md)

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Создание родных библиотек и библиотек Windows Runtime

1. В меню-баре выберите **File** > **New** > **Project.**

2. В списке шаблонов расширьте **visual C'S** > **Windows Universal,** а затем выберите шаблон **DLL (Windows Universal Apps).** В поле **Имя,** укажите, `NativeMath`а затем выбрать кнопку **OK.**

3. Обновление *NativeMath.h* в соответствии со следующим кодом.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. Обновление *NativeMath.cpp,* чтобы соответствовать этому коду:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. В **Solution Explorer**откройте меню ярлыка для решения **'NativeMath',** а затем выберите **Добавить** > **новый проект.**

6. В списке шаблонов расширьте **Visual C,** а затем выберите шаблон **компонента Выполнения Windows.** В поле **Имя,** укажите, `NativeMathWRT`а затем выбрать кнопку **OK.**

7. Обновление *Class1.h в соответствии* с этим кодом:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. Обновление *Class1.cpp* в соответствии с этим кодом:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. В строке меню последовательно выберите **Сборка** > **Собрать решение**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>Создание проекта расширения NativeMathVSIX

1. В **Solution Explorer**откройте меню ярлыка для решения **'NativeMath',** а затем выберите **Добавить** > **новый проект.**

2. В списке шаблонов расширьте расширяем**расширяемость** **Visual C,** > а затем выберите **VSIX Project.** В поле **Name** укажите **NativeMathVSIX,** а затем выберите кнопку **OK.**

3. В **Solution Explorer**откройте меню ярлыка для **source.extension.vsixmanifest,** а затем выберите View **Code.**

4. Используйте следующий XML для замены существующего XML.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. В **Solution Explorer**откройте меню ярлыка для проекта **NativeMathVSIX,** а затем выберите **Добавить** > **новый элемент.**

6. В списке **элементов Visual C,** расширьте **данные,** а затем выберите **XML-файл.** В поле **Имя,** укажите, `SDKManifest.xml`а затем выбрать кнопку **OK.**

7. Используйте этот XML для замены содержимого файла:

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. В **Solution Explorer**, в рамках проекта **NativeMathVSIX,** создайте эту структуру папок:

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

9. В **Solution Explorer**откройте меню ярлыка для решения **'NativeMath',** а затем выберите **Open Folder в File Explorer.**

10. В **Файл Explorer**, скопировать $SolutionRoot $ " *РоднойMath'NativeMath.h*, а затем в **решении Explorer**, в рамках проекта **NativeMathVSIX,** вставьте его в *$SolutionRoot $ .\\ *

     Копировать *$SolutionRoot $ »Debug-NativeMath-NativeMath.lib*, а затем вставьте его в *$SolutionRoot $ » РоднойMathVSIX -DesignTime»Debug-x86\\ * папку.

     Копируйте *$SolutionRoot $SolutionRoot.* *\\ *

     Копирование *$SolutionRoot $ »Debug-NativeMathWRT-NativeMathWRT.dll* и вставьте его в *$SolutionRoot $ » РоднойMathVSIX-Redist-Debug-x86* папки.
     Копирование *$SolutionRoot $ »Debug-NativeMathWRT-NativeMathWRT.winmd* и вставьте его в *$SolutionRoot $ » РоднойMathVSIX -Ссылки »Общая Конфигурация »Нейтральная* папка.

     Копировать *$SolutionRoot$ и debug-NativeMathWRT-NativeMathWRT.pri* и вставьте его в *$SolutionRoot $ .*

11. В *$SolutionRoot папке «NativeMathVSIX»DesignTime-Debug-x86\\ * создайте текстовый файл под названием *NativeMathSDK.props,* а затем вставьте в нем следующее содержимое:

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. В панели меню выберите **View** > **Other Windows** > **Properties Window** (клавиатура: Выберите ключ **F4).**

13. В **Solution Explorer**выберите файл **NativeMathWRT.winmd.** В окне **Свойств** измените свойство **Build Action** на **содержимое,** а затем измените **свойство «Включить» в свойство VSIX** на **True.**

     Повторите этот процесс для файла **NativeMath.h.**

     Повторите этот процесс для файла **NativeMathWRT.pri.**

     Повторите этот процесс для файла **NativeMath.Lib.**

     Повторите этот процесс для файла **NativeMathSDK.props.**

14. В **Solution Explorer**выберите файл **NativeMath.h.** В окне **Свойств** изменить Включение в свойство **VSIX** на **True.**

     Повторите этот процесс для файла **NativeMath.dll.**

     Повторите этот процесс для файла **NativeMathWRT.dll.**

     Повторите этот процесс для файла **SDKManifest.xml.**

15. В строке меню последовательно выберите **Сборка** > **Собрать решение**.

16. В **Solution Explorer**откройте меню ярлыка для проекта **NativeMathVSIX,** а затем выберите **Open Folder в File Explorer.**

17. В **файле Explorer**, перейдите к *$SolutionRoot $ »NativeMathVSIX-бин-Дебуг* папки, а затем запустить *NativeMathVSIX.vsix,* чтобы начать установку.

18. Выберите кнопку **«Установка»,** подождите, пока установка закончится, а затем откройте Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Для создания примера приложения, используюшего библиотеку классов

1. В меню-баре выберите **File** > **New** > **Project.**

2. В списке шаблонов расширьте **Visual C'** > **Windows Universal,** а затем выберите **Blank App**. В поле **Name** укажите **NativeMathSDKSample,** а затем выберите кнопку **OK.**

3. В **Solution Explorer**откройте меню ярлыка для проекта **NativeMathSDKSample,** а затем выберите **Добавить** > **ссылку.**

4. В **Add Reference** диалоговом окне Добавления, в списке типов ссылок, расширьте **универсальные Windows,** а затем выберите **расширения.** Наконец, выберите флажок **Native Math SDK,** а затем выберите кнопку **OK.**

5. Отобразите свойства проекта для NativeMathSDKSample.

    Свойства, определенные в *NativeMathSDK.props,* были применены при добавлении ссылки. Вы можете проверить свойства, которые были применены, изучив свойство **каталогов vc's** Configuration **Properties**проекта.

6. В **Solution Explorer,** откройте **MainPage.xaml,** а затем используйте следующий XAML для замены его содержимого:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. Обновление *Mainpage.xaml.h в соответствии* с этим кодом:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. Обновление *MainPage.xaml.cpp* в соответствии с этим кодом:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. Выберите ключ **F5** для запуска приложения.

10. В приложении введите любые два номера, **=** выберите операцию, а затем выберите кнопку.

     Появляется правильный результат.

    Это пошаговое позвонок показал, как [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] создать и использовать[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] расширение SDK для вызова в библиотеку и не-библиотеки.

## <a name="next-steps"></a>Следующие шаги

## <a name="see-also"></a>См. также
- [Прохождение: Создание SDK с использованием C или Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Создание комплекта для разработки программного обеспечения](../extensibility/creating-a-software-development-kit.md)
