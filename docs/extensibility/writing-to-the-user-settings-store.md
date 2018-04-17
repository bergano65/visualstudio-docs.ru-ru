---
title: Запись в хранилище настроек пользователя | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0e205fa8850bdd5ee664f66c6d6bb7bf86195bfd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="writing-to-the-user-settings-store"></a>Запись в хранилище настроек пользователя
Пользовательские параметры, доступные для записи параметров как в **Сервис / Параметры** диалоговое окно свойств windows и некоторых других диалоговых окон. Расширения Visual Studio может использовать для хранения небольших объемов данных. В этом пошаговом руководстве показано, как добавить «Блокнот» в Visual Studio в качестве внешнего средства, чтение и запись в хранилище настроек пользователя.  
  
### <a name="backing-up-your-user-settings"></a>Резервное копирование Your параметров пользователя  
  
1.  Необходимо сбросить параметры внешних инструментов, чтобы выполнять отладку и повторите эту процедуру. Чтобы сделать это, необходимо сохранить исходные параметры, чтобы можно было восстановить их при необходимости.  
  
2.  Откройте Regedit.exe.  
  
3.  Перейдите в HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\\.  
  
    > [!NOTE]
    >  Убедитесь, что вы находитесь на ключ, который содержит \14.0Exp\ и не \14.0\\. При запуске экспериментальный экземпляр Visual Studio в пользовательских настройках находятся в кусте реестра «14.0Exp».  
  
4.  Щелкните правой кнопкой мыши подраздел \External Tools\ и нажмите кнопку **Экспорт**. Убедитесь, что **Выбранная ветвь** выбран.  
  
5.  Сохраните полученный файл внешних Tools.reg.  
  
6.  Позже, при необходимо сбросить параметры внешних инструментов, выберите раздел реестра HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\ и нажмите кнопку **удалить** контекстного меню.  
  
7.  Когда **подтверждение удаления раздела** диалоговое окно, нажмите кнопку **Да**.  
  
8.  Щелкните правой кнопкой мыши файл внешних Tools.reg сохраненный ранее, щелкните **открыть с помощью**, а затем нажмите кнопку **редактора реестра**.  
  
## <a name="writing-to-the-user-settings-store"></a>Запись в хранилище настроек пользователя  
  
1.  Создайте проект VSIX с именем UserSettingsStoreExtension, а затем добавьте пользовательскую команду с именем UserSettingsStoreCommand. Дополнительные сведения о том, как создать настраиваемую команду см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  В UserSettingsStoreCommand.cs, добавьте следующие операторы using:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  В MenuItemCallback удалите тело метода и получение пользователя, параметры хранения, как показано ниже:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  Теперь Узнайте ли Блокнот уже задано в качестве внешнего средства. Необходимо пройти все внешние средства, чтобы определить, является ли параметр ToolCmd «Блокнот», следующим образом:  
  
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
  
5.  Если Блокнот не было установлено в качестве внешнего средства, задайте его следующим образом:  
  
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
  
6.  Тестирование кода. Помните, добавляет Блокнот как внешнего средства, поэтому необходимо выполнить откат реестра перед его запуском еще раз.  
  
7.  Создание кода и начните отладку.  
  
8.  На **средства** меню, нажмите кнопку **UserSettingsStoreCommand вызова**. При этом будет добавлено блокноте, чтобы **средства** меню.  
  
9. Теперь вы увидите Блокнот Сервис / Параметры меню и выбрав пункт **Блокнот** следует подключить экземпляр блокнота.