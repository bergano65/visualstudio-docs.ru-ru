---
title: Установка настраиваемой начальной страницы или изменение автозапускаемого элемента
ms.date: 02/01/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3514effbe9b8affd870e46746b308216a80de33
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864794"
---
# <a name="customize-the-start-page-for-visual-studio"></a>Настройка начальной страницы в Visual Studio

Настроить начальную страницу Visual Studio можно, например, с помощью диалогового окна **Открытие проекта** или решения, загруженного последним. Также можно отобразить настраиваемую начальную страницу, т. е. страницу XAML Windows Presentation Foundation (WPF), которая открывается в окне инструментов и может использоваться для выполнения внутренних команд Visual Studio.

## <a name="to-change-the-startup-item"></a>Изменение автозапускаемого элемента

1. В строке меню выберите **Сервис** > **Параметры**.

1. Разверните меню **Среда** и выберите **Запуск**.

1. В списке **При запуске** выберите элемент, который будет отображаться после запуска Visual Studio.

## <a name="to-show-a-custom-start-page"></a>Отображение настраиваемой начальной страницы

Вы можете [создать собственную настраиваемую начальную страницу](../extensibility/creating-a-custom-start-page.md) с помощью пакета SDK для Visual Studio или использовать уже созданную кем-то. Например, настраиваемые начальные страницы можно выбрать в [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Чтобы установить пользовательскую начальную страницу, откройте файл *VSIX* или скопируйте и вставьте файлы начальной страницы в папку *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* на компьютере.

### <a name="to-select-which-custom-start-page-to-display"></a>Выбор настраиваемой начальной страницы для отображения

1. В строке меню выберите **Сервис** > **Параметры**.

1. Разверните меню **Среда** и выберите **Запуск**.

1. В списке **Настроить начальную страницу** выберите нужную страницу.

> [!NOTE]
> Если ошибка в настраиваемой начальной странице вызывает сбой Visual Studio, можно запустить Visual Studio в безопасном режиме, а затем настроить использование начальной страницы по умолчанию. См. раздел [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>См. также

- [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md)