---
title: Создание расширения с командой меню (ru) Документы Майкрософт
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da1be8c6e00efd5d9ac94e53bf551d82d0f17ca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739559"
---
# <a name="create-an-extension-with-a-menu-command"></a>Создание расширения с командой меню

В этом пошаговом показании, как создать расширение с командой меню, которая запускает блокнот.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-menu-command"></a>Создание команды меню

1. Создайте проект VSIX под названием **FirstMenuCommand**. Шаблон проекта VSIX можно найти в диалоге **нового проекта,** ища "vsix".

2. Когда проект откроется, добавьте шаблон пользовательского элемента команд под названием **FirstCommand.** В **Solution Explorer**, правой кнопкой мыши узла проекта и выберите **Добавить** > **новый пункт**. В диалоге **Добавить новый элемент** перейдите на **Visual C е** > **Extensibility** и выберите **пользовательские команды.** В поле **«Имя»** в нижней части окна измените имя файла команды на *FirstCommand.cs.*

3. Выполните сборку решения и запустите отладку.

    Появляется экспериментальный экземпляр Visual Studio. Для получения дополнительной информации об экспериментальном экземпляре [см.](../extensibility/the-experimental-instance.md)

::: moniker range="vs-2017"

4. В экспериментальном примере откройте окно расширения и обновления **инструментов.** > **Extensions and Updates** Вы должны увидеть расширение **FirstMenuCommand** здесь. (Если вы **откроете расширения и обновления** в рабочем экземпляре Visual Studio, вы не **увидите FirstMenuCommand).**

::: moniker-end

::: moniker range=">=vs-2019"

4. В экспериментальном примере откройте окно **Extensions** > **Manage Extensions.** Вы должны увидеть расширение **FirstMenuCommand** здесь. (Если вы откроете **расширения управления** в рабочем экземпляре Visual Studio, вы не увидите **FirstMenuCommand).**

::: moniker-end

Теперь перейдите в меню **Tools** в экспериментальном экземпляре. Вы должны увидеть команду **Invoke FirstCommand.** На данный момент, команда воспитывает сообщение окно, которое говорит **FirstCommandPackage Внутри FirstMenuCommand.FirstCommand.MenuItemCallback ()**. Мы увидим, как на самом деле начать Блокнот из этой команды в следующем разделе.

## <a name="change-the-menu-command-handler"></a>Изменение обработчика команды меню

Теперь давайте обновим обработчик команды, чтобы запустить блокнот.

1. Прекратите отладку и вернитесь к рабочему экземпляру Visual Studio. Откройте *файл FirstCommand.cs* и добавьте следующее с помощью оператора:

    ```csharp
    using System.Diagnostics;
    ```

2. Найдите частного конструктора FirstCommand. Здесь команда подключена к службе команд и указан обработчик команды. Измените имя обработчика команд на StartNotepad следующим образом:

    ```csharp
    private FirstCommand(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        CommandID menuCommandID = new CommandID(CommandSet, CommandId);
        // Change to StartNotepad handler.
        MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

3. Удалите `MenuItemCallback` метод `StartNotepad` и добавьте метод, который просто запустит Блокнот:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Теперь попробуйте его. При начале отладки проекта и нажмите **Инструменты** > **Invoke FirstCommand,** вы должны увидеть экземпляр блокнот придумать.

    Вы можете использовать экземпляр <xref:System.Diagnostics.Process> класса для выполнения любой исполняемой, а не только Notepad. Попробуйте, `calc.exe`например, с.

## <a name="clean-up-the-experimental-environment"></a>Очистка экспериментальной среды

Если вы разрабатываете несколько расширений или просто изучаете результаты с различными версиями кода расширения, экспериментальная среда может перестать работать так, как должна. В этом случае следует запустить скрипт сготовона. Она называется **перезагрузка Visual Studio Экспериментальное Instance**, и он поставляется как часть визуальной студии SDK. Этот скрипт удаляет все ссылки на ваши расширения из экспериментальной среды, так что вы можете начать с нуля.

Вы можете добраться до этого сценария одним из двух способов:

1. С рабочего стола, найти **Сбросить Visual Studio Экспериментальное Instance**.

2. Выполните следующую команду в командной строке:

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Развертывание расширения

Теперь, когда у вас есть расширение инструмента работает так, как вы хотите, пришло время подумать о совместном использовании его с друзьями и коллегами. Это просто, до тех пор, как они Visual Studio 2015 установлен. Все, что вам нужно сделать, это отправить им *файл .vsix* вы построили. (Не забудьте построить его в режиме выпуска.)

Вы можете найти файл *.vsix* для этого расширения в каталоге бен *FirstMenuCommand.* В частности, если вы построили конфигурацию выпуска, она будет в:

*\<код-каталог> »FirstMenuCommand»FirstMenuCommand»-Релиз » FirstMenuCommand.vsix*

Чтобы установить расширение, ваш друг должен закрыть все открытые экземпляры Visual Studio, а затем дважды щелкните файл *.vsix,* который воспитывает **VSIX Установщик.** Файлы копируются в *версию %LocalAppData%\<-Microsoft-VisualStudio> каталог расширения.*

Когда ваш друг поднимает Visual Studio снова, они найдут расширение FirstMenuCommand в **расширениях** > **и обновлениях инструментов.** Они могут перейти к **расширениям и обновлениям,** чтобы удалить или отключить расширение, тоже.

## <a name="next-steps"></a>Следующие шаги

Это пошаговое походе показало вам лишь малую часть того, что вы можете сделать с расширением Visual Studio. Вот краткий список других (разумно легко) вещей, которые вы можете сделать с Visual Studio расширений:

1. Вы можете сделать гораздо больше вещей с простой командой меню:

   1. Добавить свой собственный значок: [Добавить значки в меню команд](../extensibility/adding-icons-to-menu-commands.md)

   2. Изменение текста команды меню: [Изменение текста команды меню](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Добавьте ярлык меню в команду: [привязать ярлыки клавиатуры к элементам меню](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Добавление различных видов команд, меню и наборов инструментов: [Расширьте меню и команды](../extensibility/extending-menus-and-commands.md)

3. Добавьте окна инструментов и расширьте встроенные окна инструментов Visual Studio: [Расширьте и настройте окна инструмента](../extensibility/extending-and-customizing-tool-windows.md)

4. Добавьте IntelliSense, предложения по коду и другие функции в существующие редакторы кода: [Расширьте службы редактора и языка](../extensibility/extending-the-editor-and-language-services.md)

5. Добавление страниц options and Property и пользовательских параметров в расширение: [расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md) и расширение [пользовательских настроек и параметров](../extensibility/extending-user-settings-and-options.md)

   Другие виды расширений требуют немного больше работы, такие как создание нового типа проекта ([Extend projects](../extensibility/extending-projects.md)), создание нового типа редактора ([Создание пользовательских редакторов и дизайнеров](../extensibility/creating-custom-editors-and-designers.md)), или реализация расширения в изолированной оболочке: [Visual Studio изолированной оболочки](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
