---
title: Шаг 2. Создание первого веб-приложения ASP.NET Core
description: С помощью этого видеоурока и пошаговых инструкций создайте свое первое веб-приложение ASP.NET Core.
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
ms.openlocfilehash: e560d9028a7c2044964f5a2ec54e8daefea26372
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922810"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>Шаг 2. Создание первого веб-приложения ASP.NET Core

С помощью этого видеоурока и пошаговых инструкций создайте свое первое веб-приложение ASP.NET Core.

_Выполните инструкции из этого видео, чтобы создать первое приложение ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>Запуск Visual Studio 2019 и создание проекта

Запустите Visual Studio 2019 и щелкните **Создать проект**. Выберите **Веб-приложение ASP.NET Core**. Выберите шаблон **Веб-приложение** и оставьте имя и расположение проекта по умолчанию. В раскрывающемся списке с версией ASP.NET Core выберите **ASP.NET Core 2.1** или **ASP.NET Core 2.2**. Нажмите кнопку **Создать**. Более подробные инструкции см. [в предыдущем видео в этой серии учебников](tutorial-aspnet-core-ef-step-01.md).

![Выбор параметров проекта ASP.NET Core в Visual Studio 2019](media/vs-2019/vs2019-choose-aspnetcore-project.png)

> [!WARNING]
> Убедитесь, что выбрали ASP .NET Core 2.1 или ASP.NET Core 2.2. Этот учебник несовместим с ASP.NET Core 3.x.

## <a name="explore-the-new-project"></a>Изучение нового проекта

В окне обозревателя решений справа можно просмотреть содержимое нового проекта. Оно описано ниже.

![Visual Studio 2019. Проект ASP.NET Core](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>wwwroot

Папка *wwwroot* содержит статические файлы, которые будут общедоступными в веб-приложении. Как правило, она содержит таблицы стилей, файлы сценария на стороне клиента и изображения.

### <a name="pages"></a>Pages

Папка *Pages* содержит страницы Razor Pages сайта. Шаблон по умолчанию предоставляет несколько страниц, включая страницу *Index.cshtml*, которая является домашней страницей приложения, а также страницы "О приложении", "Контактная информация" и т. д.

### <a name="appsettingsjson"></a>appsettings.json

Этот файл содержит параметры конфигурации сайта в формате JSON.

### <a name="programcs"></a>Program.cs

Этот файл является точкой входа для приложения. При запуске приложения первым запускается метод Main. Он создает веб-узел, который будет содержать приложение.

### <a name="startupcs"></a>Startup.cs

Веб-узел, созданный в *Program.cs*, ссылается на класс Startup и вызывает его методы для настройки приложения. Метод ConfigureServices отвечает за настройку всех служб, которые приложение будет использовать. Метод `Configure` настраивает конвейер HTTP-запросов приложения. Каждый запрос проходит через этот конвейер, при этом взаимодействуя с каждым *ПО промежуточного слоя*.

### <a name="indexcshtml"></a>Index.cshtml

Домашняя страница сайта включает в себя некоторые разметки HTML и коды Razor на стороне сервера. Она использует Razor для указания модели страницы, `IndexModel`, которая расположена в связанном файле *Index.cshtml.cs*. Она также задает заголовок страницы, устанавливая значение во ViewData. Это значение ViewData считывается в файле *\_Layout.cshtml*, расположенном в папке Shared в папке Pages. Файл макета используется несколькими страницами Razor Pages и описывает общий внешний вид приложения. Содержимое каждой страницы отображается в HTML файла макета.

## <a name="run-the-application"></a>Запуск приложения

Теперь запустите приложение и просмотрите его в браузере. Вы можете запустить приложение с помощью **CTRL**+**F5** или выбрав **Отладка** > **Запуск без отладки** в меню Visual Studio.

## <a name="customize-the-application"></a>Настройка приложения

Добавьте свойство в файл *Index.cshtml.cs* и установите для его значения текущее время в обработчике `OnGet`:

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

Замените содержимое `<div>` в файле *Index.cshtml* следующей разметкой:

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

Снова запустите приложение. Вы увидите, что страницы теперь отображают текущее время, но это всегда полночь! Это неправильно.

![Снимок экрана: домашняя страница приложения в окне браузера. Текст содержимого страницы: "На сервере сейчас 12:00!".](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>Отладка приложения

Добавьте точку останова в метод `OnGet`, где мы присваиваем значение `Time`, и на этот раз запустите отладку приложения.

Выполнение останавливается на этой строке, и вы увидите, что `DateTime.Today` включает дату, но время всегда установлено на полночь, поскольку строка не включает данные о времени.

![Снимок экрана: код для Index.cshtml.cs в Visual Studio. Точка останова установлена в строке "Time = DateTime.Today.ToShortTimeString();".](media/vs-2019/vs2019-breakpoint.png)

Измените код, чтобы использовать `DateTime.Now`, и продолжите выполнение. Новый код для `OnGet`:

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

Теперь вы увидите фактическое время сервера в браузере при переходе к приложению.

> [!NOTE]
> Выходные данные могут отличаться от показанных на рисунке, так как формат вывода ToShortDateTimeString зависит от текущих настроек языка и региональных параметров. См. раздел <xref:System.DateTime.ToShortTimeString>.

![Снимок экрана: домашняя страница приложения в окне браузера. Текст содержимого страницы: "На сервере сейчас 1:46!".](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>Дальнейшие действия

В следующем видео вы узнаете, как добавить поддержку данных в приложение.

[Учебник. Работа с данными в приложении ASP.NET Core](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>См. также раздел

- [Учебник. Создание веб-приложения Razor Pages с помощью ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)
