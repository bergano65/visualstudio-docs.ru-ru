---
title: Создание приложения ASP.NET Core с помощью TypeScript
description: В этом руководстве создается приложение с помощью ASP.NET Core и TypeScript
ms.date: 01/03/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 40011b035afdf4a04eb760d13c001e39d9c578c4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75810587"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Учебник. Создание приложения ASP.NET Core с помощью TypeScript в Visual Studio

В этом учебнике по ASP.NET Core разработки Visual Studio и TypeScript вы создадите простое веб-приложение, добавите код TypeScript, а затем запустите приложение. 

::: moniker range="vs-2017"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), если еще не сделали этого.

::: moniker-end

::: moniker range="vs-2019"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads), если еще не сделали этого.

::: moniker-end

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
> * Создать проект ASP.NET Core.
> * Добавить пакет NuGet для поддержки TypeScript.
> * Добавить код TypeScript.
> * Запуск приложения

## <a name="prerequisites"></a>Предварительные требования

* У вас должны быть установлены решение Visual Studio и рабочая нагрузка ASP.NET для разработки веб-приложений.

    ::: moniker range=">=vs-2019"
    Установите Visual Studio 2019 бесплатно со страницы  [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/) , если вы еще не сделали этого.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Установите Visual Studio 2017 бесплатно со страницы  [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/) , если вы еще не сделали этого.
    ::: moniker-end

    Если вам нужно установить рабочую нагрузку, но вы уже используете Visual Studio, выберите пункт **Средства** > **Получить средства и компоненты...** , после чего запустится Visual Studio Installer. Выберите рабочую нагрузку **ASP.NET и разработка веб-приложений**, а затем щелкните **Изменить**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Создание проекта ASP.NET Core MVC

Visual Studio управляет файлами для отдельного приложения в *проекте*. Проект включает исходный код, ресурсы и файлы конфигурации.

В этом учебнике вы начнете работу с простого проекта, содержащего код для приложения ASP.NET Core MVC.

1. Запустите Visual Studio.

1. Создайте новый проект.

    ::: moniker range=">=vs-2019"
    Нажмите клавишу **ESC**, чтобы закрыть окно запуска. Нажмите клавиши **CTRL+Q**, чтобы открыть поле поиска, введите **asp.net** и выберите **ASP.NET Core Web Application — C#** (Веб-приложение ASP.NET Core — C#). В появившемся диалоговом окне выберите **Создать**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    В верхней строке меню последовательно выберите **Файл**  > **Создать**  > **Проект**. В левой панели диалогового окна **Новый проект** разверните узел **Visual C#** и выберите **.NET Core**. В средней области выберите **ASP.NET Core Web Application — C#** (Веб-приложение ASP.NET Core — C#) и нажмите кнопку **ОК**.
    ::: moniker-end
    Если шаблон проекта **Веб-приложение ASP.NET Core** отсутствует, его можно получить, добавив рабочую нагрузку **ASP.NET и разработка веб-приложений**. Подробные инструкции см. в разделе [с предварительными требованиями](#prerequisites).

1. Нажав кнопку **Создать**, щелкните **Веб-приложение (модель-представление-контроллер)** в диалоговом окне, а затем нажмите кнопку **Создать**.

   ![Выбор шаблона MVC](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio создаст решение и откроет проект в правой области.

## <a name="add-some-code"></a>Добавление кода

1. Выбор в обозревателе решений Щелкните правой кнопкой узел проекта и выберите **Управление пакетами NuGet**. На вкладке **Обзор** найдите **Microsoft.TypeScript.MSBuild**, а затем нажмите кнопку **Установить** справа, чтобы установить пакет.

   ![Добавление пакета NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio добавляет пакет NuGet в раздел **Зависимости** узла в обозревателе решений.

   > [!NOTE]
   > Для работы с этим учебником требуется пакет NuGet. Кроме того, в собственных приложениях может потребоваться использовать [пакет npm TypeScript](https://www.npmjs.com/package/typescript).

1. В обозревателе решений щелкните правой кнопкой мыши узел проекта и выберите **Добавить > Новая папка**. Для новой папки используйте имя *scripts*.

1. Щелкните правой кнопкой мыши папку *scripts* и выберите **Добавить > Новый элемент**. Выберите **Файл конфигурации TypeScript JSON**, а затем нажмите кнопку **Добавить**.

   Visual Studio добавит файл *tsconfig.json* в папку *scripts*. Этот файл можно использовать для [настройки параметров](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) компилятора TypeScript.

1. Откройте *tsconfig.json* и замените код по умолчанию следующим кодом.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "../wwwroot/js"
     },
     "exclude": [
       "node_modules",
       "wwwroot"
     ]
   }
   ```

   Параметр *outDir* указывает выходную папку для файлов планов JavaScript, которые преобразуются компилятором TypeScript.

   Эта конфигурация содержит основные сведения об использовании TypeScript. В других сценариях, например при использовании [gulp или веб-пакета](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), вместо пути *../wwwroot/js* может потребоваться другое промежуточное расположение для преобразованных файлов JavaScript в зависимости от средств и настроек конфигурации.

1. Щелкните правой кнопкой мыши папку *scripts* и выберите **Добавить > Новый элемент**. Выберите **Файл TypeScript**, введите *app.ts* в качестве имени файла, а затем нажмите кнопку **Добавить**.

   Visual Studio добавляет файл *app.ts* в папку *scripts*.

1. Откройте файл *app.ts* и добавьте следующий код TypeScript.

    ```ts
    function TSButton() {
       let name: string = "Fred";
       document.getElementById("ts-example").innerHTML = greeter(user);
    }

    class Student {
       fullName: string;
       constructor(public firstName: string, public middleInitial: string, public lastName: string) {
           this.fullName = firstName + " " + middleInitial + " " + lastName;
       }
    }

    interface Person {
       firstName: string;
       lastName: string;
    }

    function greeter(person: Person) {
       return "Hello, " + person.firstName + " " + person.lastName;
    }

    let user = new Student("Fred", "M.", "Smith");
    ```

    Visual Studio обеспечивает поддержку IntelliSense для кода TypeScript.

    Чтобы проверить это, удалите `.lastName` из функции `greeter`, а затем повторно введите ".", и вы увидите IntelliSense.

    ![Просмотр IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Выберите `lastName`, чтобы добавить последнее имя обратно в код.

1. Откройте папку *Views/Home*, а затем файл *index.html*.

1. Добавьте следующий HTML-код в конец файла.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Откройте папку*Views/Shared*, а затем файл *_Layout.cshtml*.

1. Добавьте следующую ссылку на скрипт перед вызовом `@RenderSection("Scripts", required: false)`:

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Построение приложения

1. Выберите **Сборка > Собрать решение**.

   Хотя приложение автоматически собирается при запуске, рассмотрим, что происходит во время процесса сборки.

1. Откройте папку *wwwroot/js* и найдите два новых файла: *app.js* и файл сопоставителя с исходным кодом *app.js.map*. Эти файлы создаются компилятором TypeScript.

   Файлы сопоставителя с исходным кодом необходимы для отладки.

## <a name="run-the-application"></a>Запуск приложения

1. Чтобы запустить приложение, нажмите клавишу **F5** (**Отладка** > **Начать отладку**).

    Приложение откроется в браузере.

    В окне браузера вы увидите заголовок **Добро пожаловать** и кнопку **Щелкните здесь**.

    ![ASP.NET Core с TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Нажмите кнопку, чтобы отобразить сообщение, указанное в файле TypeScript.

## <a name="debug-the-application"></a>Отладка приложения

1. Установите точку останова в функции `greeter` в `app.ts`, щелкнув левое поле в редакторе кода.

    ![Установка точки останова](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Нажмите клавишу **F5** для запуска приложения.

   Возможно, потребуется ответить на сообщение, чтобы включить отладку скрипта.

   Приложение останавливается в точке останова. Теперь вы можете проверять переменные и использовать функции отладчика.

## <a name="next-steps"></a>Следующие шаги

Возможно, вы захотите узнать больше об использовании TypeScript с ASP.NET Core.

> [!div class="nextstepaction"]
> [ASP.NET Core с TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
