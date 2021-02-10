---
title: Изменение процесса запуска
description: Сведения о том, как настроить интерфейс начала работы для открытия в Visual Studio нужных вам инструментов.
ms.custom: SEO-VS-2020
ms.date: 02/01/2017
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 855218fb6ff2e90cb06e0f48695b64c75e7036b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886591"
---
# <a name="customize-startup"></a>Настройка запуска

Вы можете настроить процесс запуска для Visual Studio несколькими способами, например, открыв последнее решение или просто пустую среду разработки.

::: moniker range="vs-2017"

Также можно отобразить настраиваемую начальную страницу, т. е. страницу XAML Windows Presentation Foundation (WPF), которая открывается в окне инструментов и может использоваться для выполнения внутренних команд Visual Studio.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Изменение автозапускаемого элемента

1. В строке меню выберите **Сервис** > **Параметры**.

2. Разверните меню **Среда** и выберите **Запуск**.

::: moniker range="vs-2017"

3. В списке **При запуске** выберите элемент, который будет отображаться после запуска Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

3. В списке **При запуске открыть** выберите, что должно произойти после запуска Visual Studio. Вы можете выбрать **окно запуска** (в котором можно открыть новый или существующий проект), **последние решения** или **пустую среду**.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Отображение настраиваемой начальной страницы

Вы можете [создать собственную настраиваемую начальную страницу](../extensibility/creating-a-custom-start-page.md) с помощью пакета SDK для Visual Studio или использовать уже созданную кем-то. Например, настраиваемые начальные страницы можно выбрать в [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Чтобы установить пользовательскую начальную страницу, откройте файл *VSIX* или скопируйте и вставьте файлы начальной страницы в папку *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* на компьютере.

### <a name="to-select-which-custom-start-page-to-display"></a>Выбор настраиваемой начальной страницы для отображения

1. В строке меню выберите **Сервис** > **Параметры**.

1. Разверните меню **Среда** и выберите **Запуск**.

1. В списке **Настроить начальную страницу** выберите нужную страницу.

> [!TIP]
> Если ошибка на настраиваемой странице запуска вызывает сбой Visual Studio, вы можете запустить Visual Studio в безопасном режиме, а затем настроить использование страницы запуска по умолчанию. См. раздел [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>См. также раздел

- [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end
