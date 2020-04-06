---
title: 'Пошаговый шаг: Создание SDK с помощью JavaScript (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3a3fa110bd6521443521449898474299dd267d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697506"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Пошаговый шаг: Создание SDK с помощью JavaScript
Это пошаговое решение учит, как использовать JavaScript для создания простой математики SDK в качестве расширения визуальной студии (VSIX).  Пошаговая часть разделена на следующие части:

- [Для создания проекта расширения SimpleMathVSIX SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [Для создания примера приложения, используюго SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  Для JavaScript нет типа проекта библиотеки класса. В этом пошаговом шаге файл *arithmetic.js* создается непосредственно в проекте VSIX. На практике мы рекомендуем сначала создать и протестировать файлы JavaScript и CSS в качестве приложения Магазина Windows, например, используя шаблон **Blank App,** прежде чем поместить их в проект VSIX.

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации, [см.](../extensibility/visual-studio-sdk.md)

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a>Для создания проекта расширения SimpleMathVSIX SDK

1. В меню-баре выберите **File** > **New** > **Project.**

2. В списке категорий шаблонов, в соответствии с **Visual C ,** выберите **Расширительность**, а затем выберите шаблон **проекта VSIX.**

3. В **Name** текстовом поле `SimpleMathVSIX` Name укажите и выберите кнопку **OK.**

4. Если появляется **Visual Studio Package Wizard,** выберите **кнопку «Следующая»** на странице **«Добро пожаловать»,** а затем на **странице 1 из 7**— выберите кнопку **«Завершение».**

     Несмотря на то, что **manifest Designer** открывается, мы будем держать этот пошаговый промыктый простым путем изменения манифеста файла непосредственно.

5. В **Solution Explorer**откройте меню ярлыка для файла **source.extension.vsixmanifest,** а затем выберите View **Code.** Используйте этот код для замены существующего содержимого в файле.

    ```xml
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

6. В **Solution Explorer**откройте меню ярлыка для проекта **SimpleMathVSIX,** а затем выберите **Добавить** > **новый элемент.**

7. В категории **данных** выберите файл `SDKManifest.xml` **XML,** назовите файл и выберите кнопку **«Добавить».**

8. В **Solution Explorer**откройте меню ярлыка для файла **SDKManifest.xml,** а затем выберите **Open** для отображения файла в **редакторе XML.**

9. Добавьте следующий код в файл **SDKManifest.xml.**

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. В **Solution Explorer**, в меню ярлыка для файла **SDKManifest.xml** выберите **Свойства.**

11. В окне **Свойств** установите **свойство «Включить» в свойство VSIX** до **True.**

12. В **Solution Explorer**, в меню ярлыка для проекта **SimpleMathVSIX,** **выберите Добавить** > **новый Folder**, а затем назовите папку. `Redist`

13. Добавьте субфалеры под Redist, чтобы создать эту структуру папок:

     *«Редистская»Общая Конфигурация,Нейтральная, Простоматы\\*

14. В меню ярлыка для папки **qjs\\ ** выберите **Добавить** > **новый элемент.**

15. Под **элементами Visual C '** выберите категорию **Web,** а затем выберите элемент **файла JavaScript.** Назовите файл, `arithmetic.js`а затем выберите кнопку **Добавить.**

16. Вставьте следующий код в *arithmetic.js:*

    ```csharp
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

17. В **Solution Explorer**, в меню ярлыка для файла **arithmetic.js,** выберите **Свойства**. Внести следующие изменения свойств:

    - Установите включение в свойство **VSIX** **true.**

    - Установите свойство **каталога вывода** для **копирования всегда**.

18. В **Solution Explorer**, в меню ярлыка для проекта **SimpleMathVSIX,** выберите **Сборку.**

19. После успешного завершения сборки, в меню ярлыка для проекта, выберите **Open Folder в File Explorer.** Перейдите к **qbin'debug,\\**и запустите, `SimpleMathVSIX.vsix` чтобы установить его.

20. Выберите кнопку **«Установка»** и дайте завершить установку.

21. Перезапустите Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a>Для создания примера приложения, используюго SDK

1. В меню-баре выберите **File** > **New** > **Project.**

2. В списке категорий шаблонов, под **JavaScript**, выберите **Магазин Windows**, а затем выберите шаблон **Пустое приложение.**

3. В поле **Имени** `ArithmeticUI`укажите . Выберите кнопку **ОК**.

4. В **Solution Explorer**откройте меню ярлыка для проекта **ArithmeticUI,** а затем выберите **Добавить** > **справку.**

5. Под **Windows**выберите **расширения**и обратите внимание, что **простая математика** отображается.

6. Выберите флажок **простой математики,** а затем выберите кнопку **OK.**

7. В **Solution Explorer**, под **ссылками**, обратите внимание, что **простой математике** ссылка отображается. Расширьте его и обратите внимание, что есть папка **js,\\ ** которая включает в себя **arithmetic.js**. Вы можете открыть **arithmetic.js,** чтобы подтвердить, что ваш исходный код был установлен.

8. Используйте следующий код для замены содержимого *default.htm.*

   ```html
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

9. Используйте следующий код, чтобы заменить содержимое *js'default.js*.

    ```csharp
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

10. Замените содержимое *scss'default.css* этим кодом:

    ```xml
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

11. Выберите ключ **F5** для создания и запуска приложения.

12. В приложении UI введите любые два номера, **=** выберите операцию, а затем выберите кнопку. Появляется правильный результат.

## <a name="see-also"></a>См. также
- [Создание пакета средств разработки](../extensibility/creating-a-software-development-kit.md)
