---
title: Шаг 4. Предоставление веб-API приложения ASP.NET Core
description: С помощью этого видео-урока и пошаговых инструкций добавьте веб-API в веб-приложение ASP.NET Core.
ms.custom: get-started
ms.date: 02/13/2020
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
ms.openlocfilehash: 9625ce43d94158732c2d6af738a1f1abc84f666e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878777"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>Шаг 4. Предоставление веб-API приложения ASP.NET Core

Выполните эти действия, чтобы добавить веб-API в существующее приложение ASP.NET Core.

_Выполните инструкции из этого видео, чтобы добавить поддержку веб-API в приложение ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>Открытие проекта

Откройте приложение ASP.NET Core в Visual Studio 2019. Приложение уже должно использовать EF Core для управления типами моделей, как было настроено на [шаге 3 этого руководства](tutorial-aspnet-core-ef-step-03.md).

## <a name="add-an-api-controller"></a>Добавление контроллера API

Щелкните правой кнопкой по проекту и добавьте новую папку с именем *Api*. Щелкните папку правой кнопкой и выберите **Добавить** > **Создать шаблонный элемент**. Выберите **API Controller with actions, using Entity Framework** (Контроллер API с действиями, использующий Entity Framework). Теперь выберите существующий класс модели и нажмите кнопку **Добавить**.

![Visual Studio 2019. ASP.NET Core. Шаблонный контроллер API](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>Просмотр созданного контроллера

Созданный код включает в себя новый класс контроллера. В верхней части определения класса используются два атрибута.

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

Первый из них указывает маршрут действий в этом контроллере как `api/[controller]`, что означает, если контроллер называется `GamesController`, то маршрут будет `api/Games`.

Второй атрибут, `[ApiController]`, добавляет некоторые полезные проверки в класс, например, гарантию того, что каждый метод действия включает в себя свой собственный атрибут `[Route]`.

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

Контроллер использует существующий `AppDbContext`, переданный в его конструктор. Это поле будет использоваться для работы с данными приложения каждым действием.

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

Первый метод — это простой GET-запрос, как указано с помощью атрибута `[HttpGet]`. Он не имеет никаких параметров и возвращает список всех игр в базу данных.

```csharp
// GET: api/Games/5
[HttpGet("{id}")]
public async Task<IActionResult> GetGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);

    if (game == null)
    {
        return NotFound();
    }

    return Ok(game);
}
```

Следующий метод указывает в маршруте `{id}`, который будет добавлен к маршруту после `/`, поэтому полный маршрут будет примерно таким же, как `api/Games/5`, как показано в комментарии вверху. Входные данные `id` сопоставляются с параметром `id` этого метода. Внутри метода возвращается результат `BadRequest`, если модель недействительна. В противном случае EF попытается найти запись, соответствующую указанному `id`. Если это невозможно, возвращается результат `NotFound`, в противном случае возвращается соответствующая запись `Game`.

```csharp
// PUT: api/Games/5
[HttpPut("{id}")]
public async Task<IActionResult> PutGame([FromRoute] int id, [FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    if (id != game.Id)
    {
        return BadRequest();
    }

    _context.Entry(game).State = EntityState.Modified;

    try
    {
        await _context.SaveChangesAsync();
    }
    catch (DbUpdateConcurrencyException)
    {
        if (!GameExists(id))
        {
            return NotFound();
        }
        else
        {
            throw;
        }
    }

    return NoContent();
}
```

Далее запрос `[HttpPut]` к API используется для выполнения обновлений. В тексте запроса предоставляется новая запись `Game`. Выполняется некоторая проверка и поиск ошибок, и, если все прошло успешно, запись в базе данных обновляется в соответствии со значениями, указанными в тексте запроса. В противном случае возвращается соответствующий ответ об ошибке.

```csharp
// POST: api/Games
[HttpPost]
public async Task<IActionResult> PostGame([FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    _context.Game.Add(game);
    await _context.SaveChangesAsync();

    return CreatedAtAction("GetGame", new { id = game.Id }, game);
}
```

Запрос `[HttpPost]` используется для добавления новых записей в систему. Как и в случае с `[HttpPut]`, запись добавляется в текст запроса. Если она допустима, EF Core добавляет запись в базу данных, а действие возвращает обновленную запись (с её идентификатором, сформированным базой данных) и ссылку на запись в API.

```csharp
// DELETE: api/Games/5
[HttpDelete("{id}")]
public async Task<IActionResult> DeleteGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);
    if (game == null)
    {
        return NotFound();
    }

    _context.Game.Remove(game);
    await _context.SaveChangesAsync();

    return Ok(game);
}
```

Наконец, маршрут `[HttpDelete]` используется с идентификатором для удаления записи. Если запрос действителен и запись с указанным идентификатором существует, EF Core удалит ее из базы данных.

## <a name="adding-swagger"></a>Добавление Swagger

Swagger — это инструмент для документирования и тестирования API, который можно добавить в приложение ASP.NET Core в виде набора служб и промежуточного программного обеспечения. Чтобы сделать это, щелкните правой кнопкой по проекту и выберите **Управление пакетами NuGet**. Затем щелкните **Обзор**, найдите `Swashbuckle.AspNetCore` и установите версию 4.0.1.

![Visual Studio 2019. Добавление Swashbuckle из Nuget](media/vs-2019/vs2019-nuget-swashbuckle.png)

После установки откройте `Startup.cs` и добавьте следующий код в конец метода `ConfigureServices`.

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

Также необходимо добавить `using Swashbuckle.AspNetCore.Swagger;` в верхней части файла.

Затем добавьте следующий код в метод `Configure` ​​непосредственно перед `UseMvc`.

```csharp
// Enable middleware to serve generated Swagger as a JSON endpoint.
app.UseSwagger();

// Enable middleware to serve swagger-ui (HTML, JS, CSS, etc.),
// specifying the Swagger JSON endpoint.
app.UseSwaggerUI(c =>
{
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
});
```

Теперь вы сможете скомпилировать и запустить свое приложение. В браузере перейдите к `/swagger` в адресной строке. Вы увидите список моделей и конечных точек API приложения.

![Visual Studio 2019. Страница Swagger в браузере](media/vs-2019/vs2019-swagger-browser.png)

Щелкните конечную точку в разделе Games, а затем `Try it out` и `Execute`, чтобы увидеть, как себя ведут различные конечные точки.

## <a name="next-steps"></a>Следующие шаги

В следующем видео вы узнаете, как развернуть приложение в Azure.

[Шаг 5. Развертывание приложения ASP.NET Core в Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>См. также

- [Начало работы со Swashbuckle и ASP.NET Core](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio&preserve-view=true)
- [Страницы справки по веб-API ASP.NET Core с использованием Swagger (OpenAPI)](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2&preserve-view=true)