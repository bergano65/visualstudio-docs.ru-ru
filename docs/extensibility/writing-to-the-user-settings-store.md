---
title: Запись в магазин настроек пользователя (ru) Документы Майкрософт
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bed721cc084042c3ebe57639af28b7e9f13d206
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740365"
---
# <a name="writing-to-the-user-settings-store"></a>Запись в хранилище параметров пользователя
Настройки пользователя — это настройки, находящиеся в записи, как в диалоге **«Инструменты/параметры»,** окнах свойств и некоторых других диалоговых коробках. Расширения Visual Studio могут использовать их для хранения небольших объемов данных. В этом пошаговом показании, как добавить блокнот в Visual Studio в качестве внешнего инструмента, читая и записывая в магазин настроек пользователя.

## <a name="writing-to-the-user-settings-store"></a>Запись в хранилище параметров пользователя

1. Создайте проект VSIX под названием UserSettingsStoreExtension, а затем добавьте пользовательскую команду под названием UserSettingsStoreCommand. Для получения дополнительной информации о том, как создать пользовательскую команду, [см.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. В UserSettingsStoreCommand.cs добавьте следующие директивы:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. В MenuItemCallback удалите тело метода и получите в хранилище настроек пользователя:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Теперь выясните, является ли Notepad уже установлен в качестве внешнего инструмента. Необходимо провести итерировать все внешние инструменты, чтобы определить, является ли параметр ToolCmd "Notepad", следующим образом:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already an External Tool.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }
    }

    ```

5. Если блокнот не был установлен в качестве внешнего инструмента, установите его следующим образом:

    ```vb
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already installed.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }

        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";
         if (!hasNotepad)
        {
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);

            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);
        }
    }
    ```

6. Проверьте код. Помните, что он добавляет блокнот в качестве внешнего инструмента, так что вы должны откатить реестр, прежде чем запустить его во второй раз.

7. Создайте код и начните отладку.

8. В меню **«Инструменты»** нажмите **«Вызвать UserSettingsStoreCommand».** Это добавит блокнот в меню **Инструментов.**

9. Теперь вы должны увидеть блокнот на инструменты / Параметры меню, и нажав **блокнот** должен воспитывать экземпляр блокнот.
