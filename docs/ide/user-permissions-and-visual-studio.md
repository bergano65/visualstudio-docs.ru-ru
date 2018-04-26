---
title: Разрешения пользователей и Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96835e0f884494f4a6b94aa1a311b40e8a9d8ad9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="user-permissions-and-visual-studio"></a>Разрешения пользователей и Visual Studio

Для обеспечения безопасности следует по возможности запускать Visual Studio от имени обычного пользователя.

> [!WARNING]
> Также необходимо компилировать, запускать и отлаживать только те решения Visual Studio, которые получены от надежных людей или из надежных расположений.

В интегрированной среде разработки Visual Studio можно выполнять большинство операций от имени обычного пользователя, а права администратора требуются для выполнения следующих задач:

|Область|Задача|Дополнительные сведения|
|----------|----------|--------------------------|
|Установка|Установка Visual Studio.|[Установка Visual Studio](../install/install-visual-studio.md)|
||Установка, обновление или удаление локального содержимого справки.|[Установка локального содержимого и управление им](../ide/install-and-manage-local-content.md)|
|Типы приложений|Разработка решений для SharePoint.|[Требования по разработке решений SharePoint](/office-dev/office-dev/requirements-for-developing-sharepoint-solutions)|
||Получение лицензии разработчика для [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|[Получить лицензию разработчика](http://go.microsoft.com/fwlink/?LinkID=241313)|
|Панель элементов|Добавление классических элементов управления COM на **Панель элементов**.|[Панель элементов](../ide/reference/toolbox.md)|
|Надстройки|Установка и использование надстроек, которые были созданы с помощью классической COM-модели в интегрированной среде разработки.|[Создание надстроек и мастеров](http://msdn.microsoft.com/Library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Сборка|Использование выполняющихся после сборки событий, которые регистрируют компонент.|[Сведения об этапах настраиваемой сборки и событиях сборки](/cpp/ide/understanding-custom-build-steps-and-build-events)|
||Включение этапа регистрации при сборке проектов С++.|[Сведения об этапах настраиваемой сборки и событиях сборки](/cpp/ide/understanding-custom-build-steps-and-build-events)|
|Отладка|Отладка приложений с повышенными разрешениями.|[Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)|
||Отладка приложений, выполняемых под другой учетной записью пользователя, например веб-сайтов ASP.NET.|[Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Отладка в зоне для приложений XAML-браузера (XBAP).|[Основное приложение WPF (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Использование эмулятора для отладки проектов облачных служб для Microsoft Azure.|[Отладка облачной службы в Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|
||Настройка межсетевого экрана для удаленной отладки.|[Удаленная отладка](../debugger/remote-debugging.md)|
|Средства производительности|Профилирование приложения.|[Руководство по профилированию производительности для начинающих](../profiling/beginners-guide-to-performance-profiling.md)|
|Развертывание|Развертывание веб-приложения в службах IIS на локальном компьютере.|[Развертывание веб-приложения ASP.NET у поставщика услуг размещения с использованием Visual Studio или Visual Web Developer: развертывание в IIS в качестве тестовой среды](http://go.microsoft.com/fwlink/?LinkId=266478)|

## <a name="running-visual-studio-as-an-administrator"></a>Запуск Visual Studio от имени администратора

Visual Studio можно запускать с правами администратора при каждом запуске интегрированной среды разработки или изменить ярлык приложения так, чтобы оно всегда запускалось с правами администратора. Дополнительные сведения см. в справке Windows.

### <a name="to-run-visual-studio-with-administrative-permissions"></a>Запуск Visual Studio с правами администратора

Эти инструкции предназначены для Windows 10. Для других версий Windows они аналогичны.

1. Откройте меню **Пуск** и перейдите к Visual Studio 2017.

1. При помощи щелчка правой кнопкой или контекстного меню **Visual Studio 2017** выберите **More (Дополнительно)** > **Запуск от имени администратора**.

     После запуска Visual Studio в заголовке окна после имени продукта будет указано **(Администратор)**.

## <a name="see-also"></a>См. также

- [Перенос, миграция и обновление проектов Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Установка Visual Studio](../install/install-visual-studio.md)