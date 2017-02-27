---
title: "Пошаговое руководство: Создание пакета SDK с помощью JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Пошаговое руководство: Создание пакета SDK с помощью JavaScript
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом пошаговом руководстве объясняется, как использовать JavaScript для создания простых математических SDK как с расширением Visual Studio \(VSIX\).  Пошаговое руководство состоит из следующих частей:  
  
-   [Чтобы создать проект SimpleMathVSIX расширения SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
-   [Создание примера приложения с использованием пакета SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
 Для JavaScript отсутствует тип проекта библиотеки классов. В этом пошаговом руководстве пример файла arithmetic.js создается непосредственно в проект VSIX. На практике, рекомендуется сначала создать и проверить файлы JavaScript и CSS в качестве приложения для магазина Windows — например, с помощью **пустое приложение** шаблона, прежде чем поместить их в проект VSIX.  
  
## Обязательные компоненты  
 Для выполнения данного пошагового руководства, необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации см. [SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createSimpleMathVSIX"></a> Чтобы создать проект SimpleMathVSIX расширения SDK  
  
1.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2.  В списке категорий шаблонов в разделе **Visual C\#**, выберите **расширения**, и выберите **проект VSIX** шаблона.  
  
3.  В **имя** текст укажите `SimpleMathVSIX` и выберите **ОК** кнопки.  
  
4.  Если **Мастер пакетов Visual Studio** отображается, выберите **Далее** кнопку **приветствия** страницы и затем на **страница 1 из 7**, выберите **Готово** кнопки.  
  
     Хотя **Конструктор манифеста** откроется, мы будем держать в этом пошаговом руководстве простой путем непосредственного изменения файла манифеста.  
  
5.  В **обозревателе решений**, откройте контекстное меню для файла source.extension.vsixmanifest и выберите **Просмотр кода**. Этот код можно используйте для замены существующего содержимого файла.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?> <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011"> <Metadata> <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" /> <DisplayName>Simple Math</DisplayName> <Description>Does basic arithmetic calculations.</Description> </Metadata> <Installation Scope="Global" AllUsers="true"> <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" /> </Installation> <Dependencies> <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" /> </Dependencies> <Assets> <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" /> </Assets> </PackageManifest>  
    ```  
  
6.  В **обозревателе решений**, откройте контекстное меню для проекта SimpleMathVSIX и выберите **Добавить**, **новый элемент**.  
  
7.  В **данные** категории, выберите **XML\-файл**, присвойте файлу имя `SDKManifest.xml`, и выберите **Добавить** кнопки.  
  
8.  В **обозревателе решений**, откройте контекстное меню для файла SDKManifest.xml и выберите **Откройте** для отображения файла в **Редактор XML**.  
  
9. Добавьте следующий код в файл SDKManifest.xml.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?> <FileList DisplayName="Simple Math" MinVSVersion="14.0" AppliesTo="JavaScript+WindowsAppContainer" SupportsMultipleVersions="Error" MoreInfo="http://www.msdn.microsoft.com/"> <!-- JS --> <File Content="js\arithmetic.js" /> </FileList>  
  
    ```  
  
10. В **обозревателе решений**, в контекстном меню для файла SDKManifest.xml выберите **Свойства**.  
  
11. В **Свойства** установите **Включить в VSIX** свойства **True**.  
  
12. В **Обозреватель решений**, в контекстном меню проекта SimpleMathVSIX, выберите **Добавить**, **новую папку**, а затем назовите папку `Redist`.  
  
13. Добавьте подпапки в папке Redist создать следующую структуру папок:  
  
     \\Redist\\CommonConfiguration\\Neutral\\SimpleMath\\js\\  
  
14. В контекстном меню для папки \\js\\ выберите **Добавить**, **новый элемент**.  
  
15. В разделе **элементы Visual C\#**, выберите **Web** категории, а затем выберите **файл JavaScript** элемента. Имя файла `arithmetic.js`, а затем выберите **Добавить** кнопки.  
  
16. Вставьте следующий код в arithmetic.js:  
  
    ```  
    (function (global) { "use strict"; global.Arithmetic = { add: function (firstNumber, secondNumber) { return firstNumber + secondNumber; }, subtract: function (firstNumber, secondNumber) { return firstNumber - secondNumber; }, multiply: function (firstNumber, secondNumber) { return firstNumber * secondNumber; }, divide: function (firstNumber, secondNumber) { return firstNumber / secondNumber; } }; })(this);  
  
    ```  
  
17. В **обозревателе решений**, в контекстном меню для файла arithmetic.js выберите **Свойства**. Внесите следующие изменения свойства.  
  
    -   Задайте **Включить в VSIX** свойства **True**.  
  
    -   Задайте **Копировать в выходной каталог** свойства **Всегда копировать**.  
  
18. В **обозревателе решений**, в контекстном меню проекта SimpleMathVSIX выберите **построения**.  
  
19. После успешного завершения построения в контекстном меню проекта выберите **Открыть папку в проводнике**. Перейдите к \\bin\\debug\\ и запустите `SimpleMathVSIX.vsix` установить его.  
  
20. Выберите **установки** кнопки и разрешить завершение установки.  
  
21. Перезапустите Visual Studio.  
  
##  <a name="createSampleApp"></a> Создание примера приложения с использованием пакета SDK  
  
1.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2.  В списке категорий шаблонов в разделе **JavaScript**, выберите **магазина Windows**, и выберите **пустое приложение** шаблона.  
  
3.  В **имя** укажите `ArithmeticUI`. Нажмите кнопку **ОК**.  
  
4.  В **обозревателе решений**, откройте контекстное меню для проекта ArithmeticUI и выберите **Добавить**, **ссылки**.  
  
5.  В разделе **Windows**, выберите **расширения**, и обратите внимание, что **простые математические** отображается.  
  
6.  Выберите **простые математические** флажок и нажмите кнопку **ОК** кнопки.  
  
7.  В **обозревателе решений**, в разделе **ссылки**, обратите внимание, что **простые математические** ссылка отображается. Разверните его и обратите внимание, что папка \\js\\, которая содержит arithmetic.js. Можно открыть arithmetic.js, чтобы убедиться, что исходный код был установлен.  
  
8.  Используйте следующий код, чтобы заменить содержимое default.htm.  
  
    ```  
    <!DOCTYPE html> <html> <head> <meta charset="utf-8" /> <title>ArithmeticUI</title> <!-- WinJS references --> <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" /> <script src="//Microsoft.WinJS.1.0/js/base.js"></script> <script src="//Microsoft.WinJS.1.0/js/ui.js"></script> <!-- ArithmeticUI references --> <link href="/css/default.css" rel="stylesheet" /> <script src="/js/default.js"></script> <script src="/SimpleMath/js/arithmetic.js"></script> </head> <body> <form> <div id="calculator" class="ms-grid"> <input name="firstNumber" id="firstNumber" type="number" step="any"> <div id="operators"> <button class="operator" type="button">+</button> <button class="operator" type="button">-</button> <button class="operator" type="button">*</button> <button class="operator" type="button">/</button> </div> <input id="secondNumber" type="number"> <button class="calculate" type="button">=</button> <input id="result" type="number" name="result" disabled="" readonly=""> </div> </form> </body> </html>  
    ```  
  
9. Замените содержимое \\js\\default.js, используйте следующий код.  
  
    ```  
    (function () { "use strict"; var app = WinJS.Application; var operation = null; function calculateResult() { var firstNumber = parseFloat(document.querySelector("#firstNumber").value), secondNumber = parseFloat(document.querySelector("#secondNumber").value), result = 0; if (isNaN(firstNumber) || isNaN(secondNumber)) { result = 0; } else { switch (operation) { case "+": result = Arithmetic.add(firstNumber, secondNumber); break; case "-": result = Arithmetic.subtract(firstNumber, secondNumber); break; case "*": result = Arithmetic.multiply(firstNumber, secondNumber); break; case "/": result = Arithmetic.divide(firstNumber, secondNumber); break; default: } } document.querySelector("#result").value = result.toString(); } app.onactivated = function (args) { document.querySelector("#calculator").addEventListener("click", function (event) { if (event.target.tagName.toLowerCase() === "button") { switch (event.target.className) { case "operator": operation = event.target.innerText; break; case "calculate": calculateResult(); break; default: break; } } }); }; app.start(); })();  
    ```  
  
10. Замените содержимое \\css\\default.css следующим кодом:  
  
    ```  
    form { display: -ms-grid; -ms-grid-rows: 1fr auto 1fr; -ms-grid-columns: 1fr auto 1fr; height: 100%; width: 100%; } button, input[type=number] { margin-right: 5px; -ms-grid-row-align: center; } #calculator { -ms-grid-column: 2; -ms-grid-row: 2; display: -ms-grid; -ms-grid-rows: 1fr; -ms-grid-columns: auto min-content auto auto auto; } .ms-grid input { width: 5em; } #firstNumber { -ms-grid-column: 1; -ms-grid-row-align: center; } #operators { -ms-grid-column: 2; -ms-grid-row-align: center; } #operators button.operator { margin-bottom: 5px; height: 40px; } #secondNumber { -ms-grid-column: 3; } button.calculate { -ms-grid-column: 4; -ms-grid-row-align: center; height: 40px; } #result { -ms-grid-column: 5; }  
  
    ```  
  
11. Нажмите клавишу F5, чтобы построить и запустить приложение.  
  
12. В пользовательском Интерфейсе приложения введите любых двух чисел, выберите операцию и нажмите кнопку **\=** кнопки. Отображается правильный результат.  
  
## См. также  
 [Создание средств разработки программного обеспечения](../extensibility/creating-a-software-development-kit.md)