---
title: 'Пошаговое руководство: Создание пакета SDK с использованием JavaScript | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2132269329c8b6af3ac846596adea7b3462db5bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144220"
---
# <a name="walkthrough-creating-an-sdk-using-javascript"></a>Пошаговое руководство: Создание пакета SDK с использованием JavaScript
В этом пошаговом руководстве объясняется использование JavaScript для создания простых математических SDK как Visual Studio Extension (VSIX).  Пошаговое руководство состоит из следующих частей:  
  
-   [Создание проекта SimpleMathVSIX расширения SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
-   [Создание примера приложения, использующего пакет SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
 Код JavaScript отсутствует тип проекта библиотеки классов. В этом пошаговом руководстве образец файла arithmetic.js создается непосредственно в проект VSIX. На практике, рекомендуется сначала построения и тестирования файлов JavaScript и CSS в качестве приложения для магазина Windows — например, с помощью **пустое приложение** шаблона — прежде чем поместить их в проект VSIX.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createSimpleMathVSIX"></a> Создание проекта SimpleMathVSIX расширения SDK  
  
1.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2.  В списке категорий шаблонов в **Visual C#** выберите **расширяемости**и выберите **проект VSIX** шаблона.  
  
3.  В **имя** текст укажите `SimpleMathVSIX` и выберите **ОК** кнопки.  
  
4.  Если **мастер пакетов Visual Studio** отображается, выберите **Далее** кнопку на **приветствия** страницы, а затем на **страница 1 из 7**, выберите **Готово** кнопки.  
  
     Несмотря на то что **конструктор манифеста** откроется, мы будем держать в данном пошаговом руководстве простой, напрямую изменив файл манифеста.  
  
5.  В **обозревателе решений**, откройте контекстное меню Файл source.extension.vsixmanifest и выберите **Просмотр кода**. Этот код можно используйте для замены существующего содержимого файла.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
      <Metadata>  
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />  
        <DisplayName>Simple Math</DisplayName>  
        <Description>Does basic arithmetic calculations.</Description>  
      </Metadata>  
      <Installation Scope="Global" AllUsers="true">  
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />  
      </Installation>  
      <Dependencies>  
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />  
      </Dependencies>  
      <Assets>  
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />  
      </Assets>  
    </PackageManifest>  
    ```  
  
6.  В **обозревателе решений**, откройте контекстное меню для проекта SimpleMathVSIX и затем выберите **добавить**, **новый элемент**.  
  
7.  В **данные** категории, выберите **XML-файл**, назовите файл `SDKManifest.xml`и выберите **добавить** кнопки.  
  
8.  В **обозревателе решений**, откройте контекстное меню для файла SDKManifest.xml и затем выберите **откройте** для отображения файла в **редактора XML**.  
  
9. Добавьте следующий код в файл SDKManifest.xml.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <FileList  
      DisplayName="Simple Math"  
      MinVSVersion="14.0"  
      AppliesTo="JavaScript+WindowsAppContainer"  
      SupportsMultipleVersions="Error"  
      MoreInfo="http://www.msdn.microsoft.com/">  
  
      <!-- JS -->  
      <File Content="js\arithmetic.js" />  
    </FileList>  
  
    ```  
  
10. В **обозревателе решений**, в контекстном меню для файла SDKManifest.xml выберите **свойства**.  
  
11. В **свойства** задайте **включить в VSIX** свойства **True**.  
  
12. В **обозревателе решений**, в контекстном меню для проекта SimpleMathVSIX выберите **добавить**, **новую папку**, а затем назовите папку `Redist`.  
  
13. Добавьте подпапки в папке Redist, чтобы создать следующую структуру папок:  
  
     \Redist\CommonConfiguration\Neutral\SimpleMath\js\  
  
14. В контекстном меню для папки \js\ выберите **добавить**, **новый элемент**.  
  
15. В разделе **элементы Visual C#** выберите **Web** категории, а затем выберите **файл JavaScript** элемента. Назовите файл `arithmetic.js`, а затем выберите **добавить** кнопки.  
  
16. Вставьте следующий код в arithmetic.js:  
  
    ```  
    (function (global) {  
        "use strict";  
        global.Arithmetic = {  
            add: function (firstNumber, secondNumber) {  
                return firstNumber + secondNumber;  
            },  
  
            subtract: function (firstNumber, secondNumber) {  
                return firstNumber - secondNumber;  
            },  
  
            multiply: function (firstNumber, secondNumber) {  
                return firstNumber * secondNumber;  
            },  
  
            divide: function (firstNumber, secondNumber) {  
                return firstNumber / secondNumber;  
            }  
        };  
    })(this);  
  
    ```  
  
17. В **обозревателе решений**, в контекстном меню для файла arithmetic.js выберите **свойства**. Внесите следующие изменения свойства.  
  
    -   Задать **включить в VSIX** свойства **True**.  
  
    -   Задать **Копировать в выходной каталог** свойства **всегда Копировать**.  
  
18. В **обозревателе решений**, в контекстном меню для проекта SimpleMathVSIX выберите **сборки**.  
  
19. После успешного построения, в контекстном меню для проекта, выберите **открыть папку в проводнике**. Перейдите к \bin\debug\\и запустите `SimpleMathVSIX.vsix` для ее установки.  
  
20. Выберите **установить** кнопку, чтобы установка завершена.  
  
21. Перезапустите Visual Studio.  
  
##  <a name="createSampleApp"></a> Создание примера приложения, использующего пакет SDK  
  
1.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2.  В списке категорий шаблонов в **JavaScript**выберите **магазина Windows**и выберите **пустое приложение** шаблона.  
  
3.  В **имя** укажите `ArithmeticUI`. Нажмите кнопку **ОК** .  
  
4.  В **обозревателе решений**, откройте контекстное меню для проекта ArithmeticUI и затем выберите **добавить**, **ссылка**.  
  
5.  В разделе **Windows**, выберите **расширения**и обратите внимание, что **простых математических** отображается.  
  
6.  Выберите **простые математические** флажок и нажмите кнопку **ОК** кнопки.  
  
7.  В **обозревателе решений**в разделе **ссылки**, обратите внимание, что **простых математических** отображается ссылка. Развернуть его и обратите внимание, что \js\ папку, которая содержит arithmetic.js. Вы можете открыть arithmetic.js, чтобы убедиться, что исходный код был установлен.  
  
8.  Используйте следующий код, чтобы заменить содержимое default.htm.  
  
    ```  
    <!DOCTYPE html>  
    <html>  
    <head>  
        <meta charset="utf-8" />  
        <title>ArithmeticUI</title>  
  
        <!-- WinJS references -->  
        <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />  
        <script src="//Microsoft.WinJS.1.0/js/base.js"></script>  
        <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>  
  
        <!-- ArithmeticUI references -->  
        <link href="/css/default.css" rel="stylesheet" />  
        <script src="/js/default.js"></script>  
        <script src="/SimpleMath/js/arithmetic.js"></script>  
    </head>  
    <body>  
        <form>  
        <div id="calculator" class="ms-grid">  
            <input name="firstNumber" id="firstNumber" type="number" step="any">  
            <div id="operators">  
                <button class="operator" type="button">+</button>  
                <button class="operator" type="button">-</button>  
                <button class="operator" type="button">*</button>  
                <button class="operator" type="button">/</button>  
            </div>  
            <input id="secondNumber" type="number">  
            <button class="calculate" type="button">=</button>  
            <input id="result" type="number" name="result" disabled="" readonly="">  
        </div>  
        </form>  
    </body>  
    </html>  
    ```  
  
9. Используйте следующий код для замены содержимого \js\default.js.  
  
    ```  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var operation = null;  
  
        function calculateResult() {  
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),  
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),  
                result = 0;  
  
            if (isNaN(firstNumber) || isNaN(secondNumber)) {  
                result = 0;  
            }  
            else {  
                switch (operation) {  
                    case "+":  
                        result = Arithmetic.add(firstNumber, secondNumber);  
                        break;  
                    case "-":  
                        result = Arithmetic.subtract(firstNumber, secondNumber);  
                        break;  
                    case "*":  
                        result = Arithmetic.multiply(firstNumber, secondNumber);  
                        break;  
                    case "/":  
                        result = Arithmetic.divide(firstNumber, secondNumber);  
                        break;  
                    default:  
                }  
            }  
            document.querySelector("#result").value = result.toString();  
        }  
  
        app.onactivated = function (args) {  
            document.querySelector("#calculator").addEventListener("click", function (event) {  
                if (event.target.tagName.toLowerCase() === "button") {  
                    switch (event.target.className) {  
                        case "operator":  
                            operation = event.target.innerText;  
                            break;  
                        case "calculate":  
                            calculateResult();  
                            break;  
                        default:  
                            break;  
                    }  
                }  
            });  
        };  
  
        app.start();  
    })();  
    ```  
  
10. Замените содержимое \css\default.css следующим кодом:  
  
    ```  
    form {  
        display: -ms-grid;  
        -ms-grid-rows: 1fr auto 1fr;  
        -ms-grid-columns: 1fr auto 1fr;  
        height: 100%;  
        width: 100%;  
    }  
  
    button, input[type=number] {  
        margin-right: 5px;  
        -ms-grid-row-align: center;  
    }  
  
    #calculator {  
        -ms-grid-column: 2;  
        -ms-grid-row: 2;  
        display: -ms-grid;  
        -ms-grid-rows: 1fr;  
        -ms-grid-columns: auto min-content auto auto auto;  
    }  
  
    .ms-grid input {  
        width: 5em;  
    }  
  
    #firstNumber {  
        -ms-grid-column: 1;  
        -ms-grid-row-align: center;  
    }  
  
    #operators {  
        -ms-grid-column: 2;  
        -ms-grid-row-align: center;  
    }  
  
        #operators button.operator {  
            margin-bottom: 5px;  
            height: 40px;  
        }  
  
    #secondNumber {  
        -ms-grid-column: 3;  
    }  
  
    button.calculate {  
        -ms-grid-column: 4;  
        -ms-grid-row-align: center;  
        height: 40px;  
    }  
  
    #result {  
        -ms-grid-column: 5;  
    }  
  
    ```  
  
11. Нажмите клавишу F5 для построения и запуска приложения.  
  
12. В пользовательский Интерфейс приложения введите любых двух чисел, выберите операцию и затем выберите **=** кнопки. Отображается правильный результат.  
  
## <a name="see-also"></a>См. также  
 [Создание пакета средств разработки для программного обеспечения](../extensibility/creating-a-software-development-kit.md)