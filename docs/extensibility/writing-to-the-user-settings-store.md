---
title: Запись в Store параметры пользователя | Документация Майкрософт
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe8187fe11f4818433aed847a7bc67d4a889ad3a
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206883"
---
# <a name="writing-to-the-user-settings-store"></a>Запись в хранилище параметров пользователя
Пользовательские параметры, доступные для записи параметров, такие как в **Сервис / Параметры** диалоговое окно свойств windows и некоторых других диалоговых окон. Расширения Visual Studio может использовать для хранения небольших объемов данных. В этом пошаговом руководстве показано, как добавить Блокнот для Visual Studio в качестве внешнего инструмента, чтение и запись в хранилище параметров пользователя.

## <a name="writing-to-the-user-settings-store"></a>Запись в хранилище параметров пользователя

1. Создайте проект VSIX с именем UserSettingsStoreExtension, а затем добавьте пользовательскую команду с именем UserSettingsStoreCommand. Дополнительные сведения о том, как создать настраиваемую команду см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)

2. В UserSettingsStoreCommand.cs, добавьте следующие операторы using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. В MenuItemCallback удалите тело метода и получить пользователя, параметры хранения, как показано ниже:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Теперь Узнайте ли Блокнот уже задано в качестве внешнего инструмента. Необходимо выполнить итерацию всех внешние средства, чтобы определить, является ли параметр ToolCmd «Блокнот», следующим образом:

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

5. Если блокнота еще не был установлен как внешнего средства, настройте его следующим образом:

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

6. Тестирование кода. Помните, добавляет Блокнот как внешнего средства, поэтому необходимо откатить реестра перед его запуском во второй раз.

7. Создать код и начните отладку.

8. На **средства** меню, щелкните **вызвать UserSettingsStoreCommand**. При этом будет добавлено «Блокнот», чтобы **средства** меню.

9. Теперь вы должны увидеть Блокнот в Сервис / Параметры меню и выбрав пункт **Блокнот** должен использовать экземпляр блокнота.