---
title: Начало работы с ASP.NET Core
description: В этой статье описывается начало работы с ASP.NET в Visual Studio для Mac, включая установку и создание нового проекта.
author: sayedihashimi
ms.author: sayedha
ms.date: 04/02/2019
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
ms.openlocfilehash: d0e00929de11ff3fd820670be2bb6361cfb5fa6c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405002"
---
# <a name="getting-started-with-aspnet-core"></a>Начало работы с ASP.NET Core

 Visual Studio для Mac упрощает разработку службы приложения благодаря поддержке самой новой платформы веб-разработки ASP.NET Core. Платформа ASP.NET Core выполняется на базе .NET Core — современного результата развития платформы .NET Framework и среды разработки. Она рассчитана на высокую производительность и небольшие размеры установки, а также переработана для запуска в Linux, macOS и Windows.

## <a name="installing-net-core"></a>Установка .NET Core

.NET Core 2.1 автоматически устанавливается при установке Visual Studio для Mac.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Создание приложения ASP.NET Core в Visual Studio для Mac

Откройте Visual Studio для Mac. На начальном экране выберите **Создать проект...**

![Диалоговое окно создания проекта](media/asp-net-core-2019-new-asp-core.png)

Отображается диалоговое окно "Новый проект", где можно выбрать шаблон для создания приложения.

Существует несколько проектов с готовым шаблоном для создания приложения ASP.NET Core. Эти особые значения приведены ниже.

- **.NET Core > Пусто**
- **.NET Core > API**
- **.NET Core > Веб-приложение**
- **.NET Core > Веб-приложение (модель — представление — контроллер)**

![Параметры проекта ASP.NET](media/asp-net-core-2019-new-asp-core.png)

Выберите **Пустое веб-приложение ASP.NET Core** и нажмите кнопку **Далее**. Присвойте проекту имя и нажмите кнопку **Создать**. Будет создано приложение ASP.NET Core. В левой области панели решения разверните вторую стрелку и выберите файл **Startup.cs**. Он должен выглядеть, как на рисунке ниже.

![Новое представление пустого проекта ASP.NET Core](media/asp-net-core-2019-empty-project.png)

Пустой шаблон ASP.NET Core создает веб-приложение с двумя файлами по умолчанию: **Program.cs** и **Startup.cs**, которые описаны ниже. Оно также создает папку "Зависимости", содержащую зависимости пакета NuGet для проекта, такие как ASP.NET Core, платформа .NET Core и целевые объекты MSBuild, используемые при сборке проекта:

![Отображение зависимостей на панели решения](media/asp-net-core-2019-solution-dependencies.png)

### <a name="programcs"></a>Program.cs

Откройте и просмотрите файл **Program.cs** в проекте. Обратите внимание, что в методе `Main` — входе в приложение выполняются несколько операций:

```csharp
    public class Program
    {
        public static void Main(string[] args)
        {
            CreateWebHostBuilder(args).Build().Run();
        }

        public static IWebHostBuilder CreateWebHostBuilder(string[] args) =>
            WebHost.CreateDefaultBuilder(args)
                .UseStartup<Startup>();
    }
```

Приложение ASP.NET Core создает в основном методе веб-сервер, настраивая и запуская узел с помощью экземпляра [`WebHostBuilder`](/aspnet/core/fundamentals/hosting). Этот построитель предоставляет методы, позволяющие настроить узел. В шаблоне приложения используются следующие конфигурации:

* `.UseStartup<Startup>()`. указывает класс Startup.

Тем не менее вы можете добавить дополнительные конфигурации, такие как:

* `UseKestrel`. указывает, что приложением будет использоваться сервер Kestrel.
* `UseContentRoot(Directory.GetCurrentDirectory())`. использует корневую папку веб-проекта в качестве корня содержимого приложения при запуске приложения из этой папки.
* `.UseIISIntegration()`. указывает, что приложение должно работать с IIS. Чтобы использовать IIS с ASP.NET Core, нужно указать как `UseKestrel`, так и `UseIISIntegration`.

### <a name="startupcs"></a>Startup.cs

Класс Startup для вашего приложения указывается в методе `UseStartup()` для `CreateWebHostBuilder`. Именно в этом классе вы укажете конвейер обработки запросов и настроите службы.

Откройте и просмотрите файл **Startup.cs** в проекте:

```csharp
    public class Startup
    {
        // This method gets called by the runtime. Use this method to add services to the container.
        // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
        public void ConfigureServices(IServiceCollection services)
        {
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app, IHostingEnvironment env)
        {
            if (env.IsDevelopment())
            {
                app.UseDeveloperExceptionPage();
            }

            app.Run(async (context) =>
            {
                await context.Response.WriteAsync("Hello World!");
            });
        }
    }
```

Этот класс Startup всегда должен соответствовать следующим правилам:

- Он всегда должен быть открытым.
- Он должен содержать два открытых метода: `ConfigureServices` и `Configure`.

Метод `ConfigureServices` определяет службы, которые будут использоваться приложением.

`Configure` позволяет создать конвейер запросов с помощью [ПО промежуточного слоя](/aspnet/core/fundamentals/middleware). Эти компоненты используются в конвейере приложения ASP.NET для обработки запросов и откликов. Конвейер HTTP состоит из нескольких делегатов запросов, вызываемых по очереди. Каждый из делегатов может определить, обработать ли запрос самостоятельно либо передать его в следующий делегат.

Делегаты можно настроить с помощью методов `Run`, `Map` и `Use` для `IApplicationBuilder`, но метод `Run` никогда не вызывает следующий делегат и должен всегда находиться в конце конвейера.

Метод `Configure` предварительно созданного шаблона используется для выполнения нескольких действий. Во-первых, он настраивает страницу обработки исключений для использования во время разработки. Кроме того, он отправляет отклик запрашивающей веб-странице с простым кодом "Hello World".

Этот простой проект "Hello World" может выполняться без добавления дополнительного кода. Чтобы запустить приложение, можно выбрать нужный браузер в раскрывающемся списке справа от кнопки воспроизведения или просто нажать кнопку воспроизведения (треугольная), чтобы использовать браузер по умолчанию:

![Запуск браузера](media/asp-net-web-picker.png)

Для запуска веб-проекта Visual Studio для Mac использует случайный порт. Чтобы узнать, что это за порт, откройте выходные данные приложения, указанные в разделе **Вид > Панели**. Они должны иметь приблизительно следующий вид:

![Отображение порта прослушивания в выходных данных приложения](media/asp-net-core-image6.png)

После запуска проекта веб-браузер по умолчанию должен запуститься и подключиться к URL-адресу, указанному в выходных данных приложения. Или вы можете открыть браузер по своему выбору и ввести `http://localhost:5000/`, заменив `5000` на порт, указанный Visual Studio в выходных данных приложения. Должен отображаться текст `Hello World!`:

![Отображение текста в браузере](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Добавление контроллера

Приложения ASP.NET Core используют конструктивный шаблон модель-представление-контроллер (MVC), чтобы обеспечить логическое разделение обязанностей для каждой из частей приложения. MVC состоит из следующих частей:

- **Модель**: класс, представляющий данные приложения.
- **Вид**: отображает пользовательский интерфейс приложения (который часто является данными модели).
- **Контроллер**: класс, который обрабатывает запросы браузера, реагирует на ввод данных пользователем и взаимодействие с ним.

Дополнительные сведения об использовании MVC см. в руководстве с [обзором MVC ASP.NET Core](/aspnet/core/mvc/overview).

Чтобы добавить контроллер, сделайте следующее:

1. Щелкните имя проекта правой кнопкой мыши и выберите команду **Добавить > Новые файлы**. Выберите **Общие > Пустой класс** и введите имя контроллера:

    ![Диалоговое окно "Новый файл"](media/asp-net-core-image8.png)

2. Добавьте в новый контроллер следующий код:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using System.Text.Encodings.Web;

    namespace Hello_ASP
    {
        public class HelloWorldController : Controller
        {
            //
            // GET: /HelloWorld/

            public string Index()
            {
                return "This is my default action...";
            }

        }
    }
    ```

3. Добавьте зависимость `Microsoft.AspNetCore.Mvc` в проект, щелкнув правой кнопкой мыши папку **Зависимости** и выбрав пункт **Добавить пакет...**

4. Используйте поле поиска, чтобы перейти к библиотеке NuGet для `Microsoft.AspNetCore.Mvc`, и выберите **Добавить пакет**. Установка может занять несколько минут, кроме того, вам может быть предложено принять различные лицензии для требуемых зависимостей:

    ![Добавление Nuget](media/asp-net-core-image9.png)

5. В классе Startup удалите лямбда-выражение `app.Run` и задайте используемую MVC логику маршрутизации URL-адресов, чтобы определить, какой код нужно вызывать следующим:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Не забудьте удалить лямбда-выражение `app.Run`, так как оно переопределяет логику маршрутизации.

    Чтобы определить запускаемый код, MVC использует следующий формат:

    `/[Controller]/[ActionName]/[Parameters]`

    Добавляя приведенный выше фрагмент кода, вы указываете приложению использовать по умолчанию контроллер `HelloWorld` и метод действия `Index`.

6. Добавьте вызов `services.AddMvc();` для метода `ConfigureServices`, как показано ниже:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    Вы также можете передать сведения о параметрах из URL-адреса в контроллер.

7. Добавьте в HelloWorldController другой метод, как показано ниже:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Если запустить приложение сейчас, оно должно автоматически открыть браузер:

    ![Выполнение приложения в браузере](media/asp-net-core-image13.png)

9. Если перейти по адресу `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` (заменив `xxxx` на правильный порт), вы должны увидеть следующее:

    ![Выполнение приложения в браузере с аргументами](media/asp-net-core-image10.png)

## <a name="troubleshooting"></a>Устранение неполадок

Если требуется установить .NET Core вручную в Mac OS 10.12 (Sierra) и более поздней версии, сделайте следующее:

1. Прежде чем начать установку .NET Core, убедитесь, что установлены все обновления ОС до последней стабильной версии. Это можно сделать, перейдя в приложение App Store и открыв вкладку обновлений.

2. Выполните действия, указанные на [сайте .NET Core](https://www.microsoft.com/net/core#macos).

Убедитесь, что все шаги выполнены успешно, чтобы обеспечить правильную установку .NET Core.

## <a name="summary"></a>Сводка

Это руководство содержит вводные сведения о платформе ASP.NET Core. Он описывает, что это такое, когда ее можно использовать и как работать с ней в Visual Studio для Mac.
Дополнительные сведения о дальнейших действиях см. в следующих руководствах:
- Документы по [ASP.NET Core](/aspnet/core/?view=aspnetcore-2.1#build-web-apis-and-web-ui-using-aspnet-core-mvc).
- [Создание серверных служб для собственных мобильных приложений](/aspnet/core/mobile/native-mobile-backend), где описано, как создать службу REST с помощью ASP.NET Core для приложения Xamarin.Forms.
- [Практическая лабораторная работа ASP.NET Core](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).

## <a name="related-video"></a>Связанные видео

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]
