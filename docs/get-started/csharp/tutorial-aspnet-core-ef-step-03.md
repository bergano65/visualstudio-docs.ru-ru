---
title: Шаг 3. Работа с данными в приложении ASP.NET Core
description: Начните работу с данными с помощью Entity Framework Core в веб-приложении ASP.NET Core с помощью этого видео-учебника и пошаговых инструкций.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: aa3df844d5fad5dc968a9bab5d02e9a3e8e06719
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879973"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>Шаг 3. Работа с данными с использованием Entity Framework

Выполните следующие действия, чтобы приступить к работе с данными с помощью Entity Framework Core в веб-приложении ASP.NET Core.

_Выполните инструкции из этого видео, чтобы добавить данные в приложение ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>Открытие проекта

Если вы выполняете инструкции из этих видео, откройте проект веб-приложения, созданный в предыдущем разделе. Если практический пример вы начали выполнять только здесь, необходимо создать новый проект и выбрать **Веб-приложение ASP.NET**, а затем **Веб-приложение**. Оставьте для остальных параметров значения по умолчанию.

## <a name="add-your-model"></a>Добавление модели

Первое, что необходимо сделать, чтобы работать с данными в приложении ASP.NET Core — описать, как должны выглядеть данные. Мы называем это созданием *модели* вещей, связанных с проблемой, которую мы пытаемся решить. В реальных приложениях мы добавим в эти модели пользовательскую бизнес-логику, чтобы они могли вести себя определенным образом и автоматизировать для нас задачи. В этом примере мы создадим простую систему для отслеживания настольных игр. Нам нужен класс, представляющий игры и включающий в себя некоторые свойства, которые мы хотим записать об этой игре, в частности, сколько игроков она может поддерживать. Этот класс будет отправлен в новую папку, которую мы создадим в корневом каталоге веб-проекта с именем *Models*.

```csharp
public class Game
{
    public int Id { get; set; }
    public string Title { get; set; }
    public int PublicationYear { get; set; }
    public int MinimumPlayers { get; set; }
    public int MaximumPlayers { get; set; }
}
```

## <a name="create-the-pages-to-manage-your-game-library"></a>Создание страниц для управления библиотекой игр

Теперь мы готовы к созданию страниц, которые будем использовать для управления библиотекой игр. Это может звучать устрашающе, но на самом деле это совсем просто. Сначала необходимо решить, где в нашем приложении мы пропишем эту функцию. Откройте в веб-проекте папку Pages и добавьте новую папку. Назовите ее *Games*.

Теперь щелкните правой кнопкой папку Games и выберите **Добавить** > **Создать шаблонный элемент**. Выберите Razor Pages на основе параметра **Entity Framework (CRUD)** . CRUD (Create, Read, Update, Delete) означает "создание, чтение, обновление и удаление". Этот шаблон создаст страницы для каждой из этих операций (в том числе страницу "список всех" и страницу "просмотреть подробности об элементе").

![Visual Studio 2019. ASP.NET Core. Добавление шаблонных страниц](media/vs-2019/vs2019-add-scaffold.png)

Выберите класс модели игр и используйте значок "+", чтобы добавить новый класс контекста данных. Присвойте обработчику события имя `AppDbContext`. Оставьте остальные значения по умолчанию и нажмите кнопку **Добавить**.

Вы увидите, что следующие Razor Pages добавлены в папку Games:

- Create.cshtml
- DELETE.cshtml
- Details.cshtml
- Edit.cshtml
- Index.cshtml

![Visual Studio 2019. ASP.NET Core. Шаблонные страницы](media/vs-2019/vs2019-scaffolded-pages.png)

Наряду с добавлением страниц в папку *Games*, операция формирования шаблонов добавит код в класс *Startup.cs*. Просмотрев в этом классе метод `ConfigureServices`, вы увидите, что был добавлен следующий код.

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

Вы также увидите, что в файл проекта *appsettings.json* была добавлена строка подключения `AppDbContext`.

Если запустить приложение сейчас, это может привести к сбою, поскольку база данных ещё не создана. При необходимости вы можете настроить приложение на автоматическое создание базы данных, [добавив код в Program.cs](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio&preserve-view=true#update-main).

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<Data.AppDbContext>();
            context.Database.EnsureCreated();
        }
        catch (Exception ex)
        {
            var logger = services.GetRequiredService<ILogger<Program>>();
            logger.LogError(ex, "An error occurred creating the DB.");
        }
    }

    host.Run();
}
```

Чтобы разрешить имя TypeName в приведенном выше коде, добавьте следующие операторы using в *Program.cs* в конце существующего блока операторов using:

```csharp
using Microsoft.Extensions.DependencyInjection;
using WebApplication1.Models;
```

Не забудьте указать имя проекта вместо WebApplication1 в коде.

Большая часть кода — это только обработка ошибок, а также предоставление доступа к EF Core `AppDbContext` до начала работы приложения. Важная строка — та, в которой указано `context.Database.EnsureCreated()`, благодаря чему будет создана база данных, если она еще не существует. Теперь приложение готово к запуску.

## <a name="test-it-out"></a>Тестирование приложения

Запустите приложение и перейдите к `/Games` адресной строке. Вы увидите страницу с пустым списком. Щелкните **Новый**, чтобы добавить новый список `Game` в коллекцию. Заполните форму и нажмите **Создать**. Вы должны увидеть его в представлении списка. Щелкните **Подробности**, чтобы просмотреть сведения об отдельной записи.

Добавьте еще одну запись. Можно щелкнуть *Правка* для изменения сведений о записи или **Удалить**, чтобы удалить ее, после чего вам будет предложено подтвердить действие перед удалением записи.

![Visual Studio 2019. ASP.NET Core. Шаблонные страницы в браузере](media/vs-2019/vs2019-game-list.png)

Это все, что нужно для начала работы с данными в приложении ASP.NET Core с использованием EF Core и Visual Studio 2019.

## <a name="next-steps"></a>Следующие шаги

В следующем видео вы узнаете, как добавить поддержку веб-API в приложение.

[Шаг 4. Предоставление веб-API приложения ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>См. также

- [Razor Pages с Entity Framework Core в ASP.NET Core](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio&preserve-view=true)
- [Razor Pages с EF Core в ASP.NET Core](/aspnet/core/data/?view=aspnetcore-2.1&preserve-view=true)
