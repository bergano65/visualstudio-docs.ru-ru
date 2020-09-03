---
title: Пошаговое руководство. Создание пакета SDK на C# или Visual Basic | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a604e3500c0ea438c987c4cf07ded98a5e03dd61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "77558204"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Пошаговое руководство. Создание пакета SDK с помощью C# или Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве вы узнаете, как создать простой пакет SDK для математических библиотек с помощью Visual C#, а затем упаковать пакет SDK как расширение Visual Studio (VSIX). Вы выполните следующие процедуры:  
  
- [Создание компонента среда выполнения Windows Симплемас](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
- [Создание проекта расширения Симплемасвсикс](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
- [Создание примера приложения, использующего библиотеку классов](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Предварительные условия  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a> Создание компонента среда выполнения Windows Симплемас  
  
1. В строке меню последовательно выберите пункты **файл**, **создать**, **Новый проект**.  
  
2. В списке шаблонов разверните узел **Visual C#** или **Visual Basic**, выберите узел **Магазин Windows** и выберите шаблон **компонента Среда выполнения Windows** .  
  
3. В поле **имя** укажите **симплемас**, а затем нажмите кнопку **ОК** .  
  
4. В **Обозреватель решений**откройте контекстное меню для узла проекта **симплемас** и выберите пункт **Свойства**.  
  
5. Переименуйте **Class1.CS** в **Arithmetic.CS** и обновите его, чтобы он соответствовал следующему коду:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6. В **Обозреватель решений**откройте контекстное меню узла **решения "симплемас"** и выберите **Configuration Manager**.  
  
     Откроется диалоговое окно **Configuration Manager** .  
  
7. В списке **Активная конфигурация решения** выберите **выпуск**.  
  
8. В столбце **Конфигурация** убедитесь, что для строки **симплемас** задано значение **Release**, а затем нажмите кнопку **Закрыть** , чтобы принять изменения.  
  
    > [!IMPORTANT]
    > Пакет SDK для компонента Симплемас включает только одну конфигурацию. Эта конфигурация должна быть сборкой выпуска, или приложения, использующие этот компонент, не проходят сертификацию для [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] .  
  
9. В **Обозреватель решений**откройте контекстное меню для узла проекта **симплемас** и выберите пункт **Сборка**.  
  
## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> Создание проекта расширения Симплемасвсикс  
  
1. В контекстном меню узла **решения "симплемас"** выберите **Добавить**, **Новый проект**.  
  
2. В списке шаблонов разверните узел **Visual C#** или **Visual Basic**, выберите узел **расширяемость** , а затем выберите шаблон **проекта VSIX** .  
  
3. В поле **имя** укажите **симплемасвсикс**, а затем нажмите кнопку **ОК** .  
  
4. В **Обозреватель решений**выберите элемент **source. extension. vsixmanifest** .  
  
5. В строке меню выберите **Вид**, **Код**.  
  
6. Замените существующий XML на следующий XML-код:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7. В **Обозреватель решений**выберите проект **симплемасвсикс** .  
  
8. В строке меню выберите **проект**, **Добавить новый элемент**.  
  
9. В списке **общих элементов**разверните **данные**, а затем выберите **XML-файл**.  
  
10. В поле **имя** укажите `SDKManifest.xml` , а затем нажмите кнопку **добавить** .  
  
11. В **Обозреватель решений**откройте контекстное меню для `SDKManifest.xml` , выберите пункт **Свойства**, а затем измените значение свойства **включить в VSIX** на **true**.  
  
12. Замените содержимое файла следующим XML-кодом.  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. В **Обозреватель решений**откройте контекстное меню проекта **Симплемасвсикс** , выберите **Добавить**, а затем выберите **создать папку**.  
  
14. Переименуйте папку в `references` .  
  
15. Откройте контекстное меню для папки **References** , выберите **Добавить**, а затем выберите **создать папку**.  
  
16. Переименуйте вложенную папку в `commonconfiguration` , создайте в ней вложенную папку и присвойте ей имя `neutral` .  
  
17. Повторите предыдущие четыре шага, на этот раз переименование первой папки в `redist` .  
  
     Теперь проект содержит следующую структуру папок:  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. В **Обозреватель решений**откройте контекстное меню проекта **симплемас** , а затем выберите пункт **Открыть папку в проводнике**.  
  
19. В **проводнике**перейдите в папку Bin\Release, откройте контекстное меню для файла симплемас. winmd и выберите команду **Копировать**.  
  
20. В **Обозреватель решений**вставьте файл в папку референцес\коммонконфигуратион\неутрал в проекте **симплемасвсикс** .  
  
21. Повторите предыдущий шаг, вставляя файл Симплемас. PRI в папку редист\коммонконфигуратион\неутрал в проекте **симплемасвсикс** .  
  
22. В **Обозреватель решений**выберите **симплемас. winmd**.  
  
23. В строке меню выберите **вид**, **Свойства** (клавиатура: нажмите клавишу F4).  
  
24. В окне **Свойства** измените свойство **действие сборки** на **содержимое**, а затем измените значение свойства **включить в VSIX** на **true**.  
  
25. В **Обозреватель решений**повторите эту процедуру для **симплемас. PRI**.  
  
26. В **Обозреватель решений**выберите проект **симплемасвсикс** .  
  
27. В строке меню выберите **Сборка**, **Сборка симплемасвсикс**.  
  
28. В **Обозреватель решений**откройте контекстное меню проекта **симплемасвсикс** , а затем выберите пункт **Открыть папку в проводнике**.  
  
29. В **проводнике**перейдите в папку \bin\Release и запустите симплемасвсикс. VSIX, чтобы установить его.  
  
30. Нажмите кнопку **установить** , дождитесь завершения установки, а затем перезапустите Visual Studio.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Создание примера приложения, использующего библиотеку классов  
  
1. В строке меню последовательно выберите пункты **файл**, **создать**, **Новый проект**.  
  
2. В списке шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем выберите узел **Магазин Windows** .  
  
3. Выберите шаблон **пустое приложение** , присвойте проекту имя **арисметикуи**, а затем нажмите кнопку **ОК** .  
  
4. В **Обозреватель решений**откройте контекстное меню проекта **Арисметикуи** и выберите **добавить**, **ссылка**.  
  
5. В списке ссылочных типов разверните узел **Windows**, а затем выберите **расширения**.  
  
6. В области сведений выберите расширение **простого математического пакета SDK** .  
  
    Появится дополнительная информация о пакете SDK. Можно выбрать ссылку " **Дополнительные сведения** ", которая будет открыта https://docs.microsoft.com , как указано в файле SDKManifest.xml ранее в этом пошаговом руководстве.  
  
7. В диалоговом окне **Диспетчер ссылок** установите флажок **простой математический пакет SDK** , а затем нажмите кнопку **ОК** .  
  
8. В строке меню выберите **вид**, **Обозреватель объектов**.  
  
9. В списке **Обзор** выберите **простые математические**.  
  
     Теперь вы можете исследовать, что есть в пакете SDK.  
  
10. В **Обозреватель решений**Откройте MainPage. XAML и замените его содержимое следующим кодом XAML:  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. Обновите MainPage.xaml.cs в соответствии со следующим кодом:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Нажмите клавишу F5, чтобы запустить приложение.  
  
13. В приложении введите любые два числа, выберите операцию, а затем нажмите **=** кнопку.  
  
     Появится правильный результат.  
  
    Вы успешно создали и использовали пакет SDK для расширений.  
  
## <a name="see-also"></a>См. также:  
 [Пошаговое руководство. Создание пакета SDK с помощью C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Пошаговое руководство. Создание пакета SDK с помощью JavaScript](walkthrough-creating-an-sdk-using-javascript.md)   
 [Создание пакета средств разработки для программного обеспечения](../extensibility/creating-a-software-development-kit.md)
