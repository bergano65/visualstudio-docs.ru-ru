---
title: "Запись в хранилище настроек пользователя | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 35ca397d57906a6316543325a08b118613fc2035
ms.lasthandoff: 02/22/2017

---
# <a name="writing-to-the-user-settings-store"></a>Запись в хранилище настроек пользователя
Параметры пользователя, для записи параметров в аналогичных **инструменты и параметры** диалогового окна, окна свойств и некоторых других диалоговых окон. Расширения Visual Studio может использовать для хранения небольших объемов данных. В этом пошаговом руководстве показано, как добавлять Блокнот в Visual Studio в качестве внешнего инструмента, чтение и запись в хранилище настроек пользователя.  
  
### <a name="backing-up-your-user-settings"></a>Резервное копирование параметров пользователя  
  
1.  Необходимо сбросить параметры внешних средств, можно отлаживать и повторите процедуру. Для этого необходимо сохранить первоначальные параметры, чтобы их можно было восстановить при необходимости.  
  
2.  Откройте Regedit.exe.  
  
3.  Перейдите к средствам HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External\\.  
  
    > [!NOTE]
    >  Убедитесь, что вы находитесь на ключ, который содержит \14.0Exp\ и не \14.0\\. При запуске экспериментальном экземпляре Visual Studio в кусте реестра «14.0Exp», настройки пользователя.  
  
4.  Щелкните правой кнопкой мыши подраздел \External Tools\ и нажмите кнопку **Экспорт**. Убедитесь, что **Выбранная ветвь** выбран.  
  
5.  Сохраните полученный файл внешних Tools.reg.  
  
6.  Позже, когда вы хотите сбросить параметры внешних средств, выберите раздел реестра HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\ и нажмите кнопку **удаление** в контекстном меню.  
  
7.  Когда **подтверждение удаления раздела** откроется диалоговое окно, нажмите кнопку **Да**.  
  
8.  Щелкните правой кнопкой мыши Tools.reg внешний файл, сохраненный ранее, нажмите кнопку **открыть с помощью**и нажмите кнопку **редактора реестра**.  
  
## <a name="writing-to-the-user-settings-store"></a>Запись в хранилище настроек пользователя  
  
1.  Создайте проект VSIX с именем UserSettingsStoreExtension, а затем добавьте пользовательскую команду с именем UserSettingsStoreCommand. Дополнительные сведения о создании пользовательских команд в разделе [создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  В UserSettingsStoreCommand.cs, добавьте следующие операторы using:  
  
    ```c#  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  В MenuItemCallback удалите тело метода и работу пользователя, параметры хранения, как показано ниже:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  Теперь найдите того, является ли Блокнот уже как внешняя программа. Необходимо выполнить итерацию все внешние инструменты, чтобы определить, является ли параметр ToolCmd «Блокнот», как показано ниже:  
  
    ```c#  
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
  
5.  Если блокнота еще не был установлен как внешнего инструмента, установите его следующим образом:  
  
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
  
6.  Проверьте код. Помните, добавляет Блокнот как внешнего средства, поэтому необходимо выполнить откат реестра перед запуском его во второй раз.  
  
7.  Создание кода и начать отладку.  
  
8.  На **средства** меню, щелкните **UserSettingsStoreCommand вызова**. При этом будет добавлен текстовый редактор Блокнот и **средства** меню.  
  
9. Теперь вы увидите Блокнот в Сервис / Параметры меню и затем щелкните **Блокнот** следует открыть экземпляр Notepad.
