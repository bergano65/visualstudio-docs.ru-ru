---
title: Страница "Браузер", папка "Среда", диалоговое окно "Параметры"
description: Сведения о том, как с помощью страницы "Веб-браузер" в разделе "Среда" задать параметры для внутреннего веб-браузера и для Internet Explorer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.Environment.Web Browser
- VS.ToolsOptionsPages.Environment.WebBrowser
- VS.ToolsOptionsPages.Environment.Web_Browser
helpviewer_keywords:
- browsers, customizing
- searching, search page for Web browser
- Web browsers, customizing
- searches, default Web browser search page
- URLs, specifying VS home page
- home page
- Options dialog box, Web settings
- Internet Explorer, setting options
ms.assetid: 586db4eb-032d-4cb5-93a6-a7c14de1ae49
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c87077005ae2ebbcc8fba92c9f1dc09f17bb3157
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836219"
---
# <a name="options-dialog-box-environment--web-browser"></a>Диалоговое окно "Параметры": Страница "Веб-браузер" \> папка "Среда"

Задает параметры для внутреннего веб-браузера и для Internet Explorer. Для доступа к этому диалоговому окну щелкните элемент **Параметры** в меню **Сервис**, разверните папку **Среда** и выберите **Веб-браузер**.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Сброс параметров](../environment-settings.md#reset-settings).

> [!IMPORTANT]
> При открытии определенных файлов или компонентов из Интернета на вашем компьютере может выполняться код.

## <a name="home-page"></a>Главная страница

Задает страницу, отображаемую при открытии веб-браузера интегрированной среды разработки.

## <a name="search-page"></a>Страница "Поиск"

Позволяет указать страницу поиска для внутреннего веб-браузера. Это расположение может отличаться от страницы поиска, используемый экземплярами Internet Explorer, которые запускаются за пределами интегрированной среды разработки (IDE).

## <a name="view-source-in"></a>Использовать для просмотра HTML-кода

Задает редактор, используемый для открытия веб-страницы при выборе команды **Просмотреть исходный код** на странице из внутреннего веб-браузера.

- **Редактор исходного текста**. Выберите для просмотра исходного кода в [редакторе](../../ide/writing-code-in-the-code-and-text-editor.md).

- **Редактор HTML**. Выберите для просмотра исходного кода в [конструкторе HTML](/previous-versions/ex0hkwbx(v=vs.140)). Используйте этот вариант, чтобы изменить веб-страницу в одном из двух представлений: представление конструктора или стандартное текстовое представление исходного кода.

- **Внешний редактор**. Выберите для просмотра источника в другом редакторе. Укажите путь к любому редактору, например Notepad.exe.

## <a name="internet-explorer-options"></a>Параметры Internet Explorer

Щелкните, чтобы изменить параметры Internet Explorer в диалоговом окне **Свойства браузера**. Изменения, внесенные в этом диалоговом окне, влияют как на внутренний веб-браузер, так и на экземпляры Internet Explorer, запущенные вне среды IDE Visual Studio (например, из меню "Пуск").

> [!NOTE]
> В окне **Просмотр с помощью** можно выбрать вместо внутреннего веб-браузера Visual Studio браузер, который вы предпочитаете. Открыть диалоговое окно "Просмотр с помощью" можно из контекстного меню, например HTML-файла проекта.

## <a name="see-also"></a>См. также

- [Страница "Общие", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/general-environment-options-dialog-box.md)
- [Конструктор HTML](/previous-versions/ex0hkwbx(v=vs.140))