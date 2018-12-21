---
title: Запись в Store параметры пользователя | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 70522d8a291cad559a042dab7f4eeb3c3c4684ac
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779727"
---
# <a name="writing-to-the-user-settings-store"></a>Запись в хранилище параметров пользователя
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пользовательские параметры, доступные для записи параметров, такие как в **Сервис / Параметры** диалоговое окно свойств windows и некоторых других диалоговых окон. Расширения Visual Studio может использовать для хранения небольших объемов данных. В этом пошаговом руководстве показано, как добавить Блокнот для Visual Studio в качестве внешнего инструмента, чтение и запись в хранилище параметров пользователя.  
  
### <a name="backing-up-your-user-settings"></a>Резервное копирование параметров пользователя  
  
1.  Необходимо сбросить параметры внешние средства, что позволяет выполнять отладку и повторите эту процедуру. Чтобы сделать это, необходимо сохранить исходные параметры таким образом, чтобы можно было восстановить при необходимости.  
  
2.  Откройте Regedit.exe.  
  
3.  Перейдите к средствам HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External\\.  
  
    > [!NOTE]
    >  Убедитесь, что вы находитесь на ключ, который содержит \14.0Exp\ и не \14.0\\. При запуске экспериментальном экземпляре Visual Studio, настройки пользователя, в кусте реестра «14.0Exp».  
  
4.  Щелкните правой кнопкой мыши подраздел \External Tools\, а затем нажмите кнопку **Экспорт**. Убедитесь, что **выбранный куст** выбран.  
  
5.  Сохраните полученный файл внешних Tools.reg.  
  
6.  Позже, когда вы хотите сбросить настройки внешних инструментов, выберите раздел реестра HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\ и нажмите кнопку **удалить** в контекстном меню.  
  
7.  Когда **подтверждение удаления ключа** появится диалоговое окно, нажмите кнопку **Да**.  
  
8.  Щелкните правой кнопкой мыши Tools.reg внешний файл, сохраненный ранее, нажмите кнопку **открыть с помощью**, а затем нажмите кнопку **редактора реестра**.  
  
## <a name="writing-to-the-user-settings-store"></a>Запись в хранилище параметров пользователя  
  
1.  Создайте проект VSIX с именем UserSettingsStoreExtension, а затем добавьте пользовательскую команду с именем UserSettingsStoreCommand. Дополнительные сведения о том, как создать настраиваемую команду см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  В UserSettingsStoreCommand.cs, добавьте следующие операторы using:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  В MenuItemCallback удалите тело метода и получить пользователя, параметры хранения, как показано ниже:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  Теперь Узнайте ли Блокнот уже задано в качестве внешнего инструмента. Необходимо выполнить итерацию всех внешние средства, чтобы определить, является ли параметр ToolCmd «Блокнот», следующим образом:  
  
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
  
5.  Если блокнота еще не был установлен как внешнего средства, настройте его следующим образом:  
  
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
  
6.  Тестирование кода. Помните, добавляет Блокнот как внешнего средства, поэтому необходимо откатить реестра перед его запуском во второй раз.  
  
7.  Создать код и начните отладку.  
  
8.  На **средства** меню, щелкните **вызвать UserSettingsStoreCommand**. При этом будет добавлено «Блокнот», чтобы **средства** меню.  
  
9. Теперь вы должны увидеть Блокнот в Сервис / Параметры меню и выбрав пункт **Блокнот** должен использовать экземпляр блокнота.

