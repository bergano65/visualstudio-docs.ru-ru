---
title: Пошаговое руководство. Создание пакета SDK с помощью C# или Visual Basic | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5989e0d72aaa7dda8e3daae16a6f384f8815357f
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002979"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Пошаговое руководство. Создание пакета SDK с помощью C# или Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве вы узнаете, как создать простой пакет SDK для математической библиотеки с помощью Visual C# и затем пакета SDK в Visual Studio Extension (VSIX). Вы выполните следующие процедуры:  
  
-   [Для создания компонента среды выполнения Windows SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [Создание проекта расширения SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
-   [Чтобы создать приложение-пример, использующий библиотеку классов](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Для создания компонента среды выполнения Windows SimpleMath  
  
1.  В строке меню выберите **файл**, **New**, **новый проект**.  
  
2.  В списке шаблонов разверните **Visual C#** или **Visual Basic**, выберите **Windows Store** узел, а затем выберите **компонента среды выполнения Windows** шаблона.  
  
3.  В **имя** укажите **SimpleMath**, а затем выберите **ОК** кнопки.  
  
4.  В **обозревателе решений**, откройте контекстное меню для **SimpleMath** узел проекта, а затем выберите **свойства**.  
  
5.  Переименуйте **Class1.cs** для **Arithmetic.cs** и измените его в следующем коде:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6.  В **обозревателе решений**, откройте контекстное меню для **решение «SimpleMath»** узел, а затем выберите **Configuration Manager**.  
  
     **Configuration Manager** откроется диалоговое окно.  
  
7.  В **активная конфигурация решения** выберите **выпуска**.  
  
8.  В **конфигурации** столбец, убедитесь, что **SimpleMath** строки равен **выпуска**, а затем выберите **закрыть** кнопку, чтобы принять изменение.  
  
    > [!IMPORTANT]
    >  Пакет SDK для компонента SimpleMath включает только одну конфигурацию. Этой конфигурации должен содержать сборку выпуска, или приложения, использующие компонент не будет передавать сертификации[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].  
  
9. В **обозревателе решений**, откройте контекстное меню для **SimpleMath** узел проекта, а затем выберите **построения**.  
  
##  <a name="createVSIX"></a> Создание проекта расширения SimpleMathVSIX  
  
1.  В контекстном меню для **решение «SimpleMath»** узел, выберите **добавить**, **новый проект**.  
  
2.  В списке шаблонов разверните **Visual C#** или **Visual Basic**, выберите **расширяемости** узел, а затем выберите **проект VSIX** шаблон.  
  
3.  В **имя** укажите **SimpleMathVSIX**, а затем выберите **ОК** кнопки.  
  
4.  В **обозревателе решений**, выберите **source.extension.vsixmanifest** элемента.  
  
5.  В строке меню выберите **Вид**, **Код**.  
  
6.  Замените существующий XML-код следующим кодом XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  В **обозревателе решений**, выберите **SimpleMathVSIX** проекта.  
  
8.  В строке меню выберите **проекта**, **Добавление нового элемента**.  
  
9. В списке **общих элементов**, разверните **данных**, а затем выберите **XML-файл**.  
  
10. В **имя** укажите `SDKManifest.xml`, а затем выберите **добавить** кнопки.  
  
11. В **обозревателе решений**, откройте контекстное меню для `SDKManifest.xml`, выберите **свойства**, а затем измените значение **включить в VSIX** свойства **True**.  
  
12. Замените содержимое файла следующим XML-кодом.  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. В **обозревателе решений**, откройте контекстное меню для **SimpleMathVSIX** проекта, выберите **добавить**, а затем выберите **новую папку**.  
  
14. Переименуйте папку в `references`.  
  
15. Откройте контекстное меню для **ссылки** папку, выберите **добавить**, а затем выберите **новую папку**.  
  
16. Переименуйте вложенную папку для `commonconfiguration`, создайте вложенную папку внутри нее и именем `neutral`.  
  
17. Повторите предыдущие четыре шага, в настоящее время переименования первой папки для `redist`.  
  
     Теперь проект содержит следующую структуру папок:  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. В **обозревателе решений**, откройте контекстное меню для **SimpleMath** проекта, а затем выберите **открыть папку в проводнике**.  
  
19. В **проводнике**, перейдите к папке bin\Release, откройте контекстное меню для файла SimpleMath.winmd и затем выберите **копирования**.  
  
20. В **обозревателе решений**, вставьте файл в папке references\commonconfiguration\neutral в **SimpleMathVSIX** проекта.  
  
21. Повторите предыдущий шаг, вставив SimpleMath.pri файл в папке redist\commonconfiguration\neutral в **SimpleMathVSIX** проекта.  
  
22. В **обозревателе решений**, выберите **SimpleMath.winmd**.  
  
23. В строке меню выберите **представление**, **свойства** (клавиатуры: Нажмите клавишу F4).  
  
24. В **свойства** измените **действие при построении** свойства **содержимого**, а затем измените **включить в VSIX** свойства  **Значение true,**.  
  
25. В **обозревателе решений**, повторите эту процедуру для **SimpleMath.pri**.  
  
26. В **обозревателе решений**, выберите **SimpleMathVSIX** проекта.  
  
27. В строке меню выберите **построения**, **построения SimpleMathVSIX**.  
  
28. В **обозревателе решений**, откройте контекстное меню для **SimpleMathVSIX** проекта, а затем выберите **открыть папку в проводнике**.  
  
29. В **проводнике**, перейдите к папке \bin\Release, а затем запустите SimpleMathVSIX.vsix, чтобы установить его.  
  
30. Выберите **установить** кнопку и дождитесь завершения установки перезапустите Visual Studio.  
  
##  <a name="createSample"></a> Чтобы создать приложение-пример, использующий библиотеку классов  
  
1. В строке меню выберите **файл**, **New**, **новый проект**.  
  
2. В списке шаблонов разверните **Visual C#** или **Visual Basic**, а затем выберите **Windows Store** узла.  
  
3. Выберите **пустое приложение** шаблон, имя проекта **ArithmeticUI**, а затем выберите **ОК** кнопки.  
  
4. В **обозревателе решений**, откройте контекстное меню для **ArithmeticUI** проекта, а затем выберите **добавить**, **ссылку**.  
  
5. В списке ссылочных типов, разверните **Windows**, а затем выберите **расширения**.  
  
6. В области сведений выберите **пакета SDK для простой математической** расширения.  
  
    Отображение дополнительных сведений о вашем пакете SDK. Вы можете выбрать **Подробнее** ссылку, чтобы открыть http://www.msdn.microsoft.com, как указано в файле SDKManifest.xml ранее в этом пошаговом руководстве.  
  
7. В **диспетчер ссылок** выберите **пакета SDK для простой математической** , а затем нажать **ОК** кнопки.  
  
8. В строке меню выберите **представление**, **обозреватель объектов**.  
  
9. В **Обзор** выберите **простых математических расчетов**.  
  
     Теперь вы можете изучить возможности пакета SDK.  
  
10. В **обозревателе решений**, откройте файл MainPage.xaml и замените его содержимое на следующий XAML:  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. Обновите MainPage.XAML, чтобы соответствовало следующему коду:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Нажмите клавишу F5, чтобы запустить приложение.  
  
13. В приложении введите любых двух чисел, выберите операцию и затем выберите **=** кнопки.  
  
     Отображается правильный результат.  
  
    Вы успешно создали и использовать пакет SDK расширения.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Создание пакета SDK с помощью C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Пошаговое руководство: Создание пакета SDK с помощью JavaScript](walkthrough-creating-an-sdk-using-javascript.md)   
 [Создание пакета средств разработки для программного обеспечения](../extensibility/creating-a-software-development-kit.md)
