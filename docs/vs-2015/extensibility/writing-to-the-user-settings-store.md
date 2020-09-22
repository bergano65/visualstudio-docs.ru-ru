---
title: Запись в хранилище параметров пользователя | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 764d9b81297c6bbefd1f5fdf7c77e4d514bb5045
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843049"
---
# <a name="writing-to-the-user-settings-store"></a>Запись в хранилище параметров пользователя
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Параметры пользователя — это доступные для записи параметры, такие как шаблоны в диалоговом окне **Сервис/параметры** , окна свойств и некоторые другие диалоговые окна. Расширения Visual Studio могут использовать их для хранения небольших объемов данных. В этом пошаговом руководстве показано, как добавить приложение "Блокнот" в Visual Studio как внешнее средство, читая данные из хранилища пользовательских параметров и записывая в него.  
  
### <a name="backing-up-your-user-settings"></a>Резервное копирование параметров пользователя  
  
1. Необходимо иметь возможность сбросить параметры внешних средств, чтобы можно было выполнить отладку и повторить процедуру. Для этого необходимо сохранить исходные параметры, чтобы при необходимости можно было восстановить их.  
  
2. Откройте Regedit.exe.  
  
3. Перейдите в раздел HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0Exp\External Tools \\ .  
  
    > [!NOTE]
    > Убедитесь, что вы просматриваете ключ, содержащий \14.0Exp\, а не \ 14,0 \\ . При запуске экспериментального экземпляра Visual Studio параметры пользователя находятся в кусте реестра с параметром "не exp".  
  
4. Щелкните правой кнопкой мыши подраздел инструменты \Екстернал и выберите пункт **Экспорт**. Убедитесь, что выбраны **выбранные ветви** .  
  
5. Сохраните полученный внешний файл Tools. reg.  
  
6. Затем, когда нужно сбросить параметры внешних средств, выберите раздел HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0Exp\External Tools \ реестр и щелкните **Удалить** в контекстном меню.  
  
7. Когда откроется диалоговое окно **Подтверждение удаления ключа** , нажмите кнопку **Да**.  
  
8. Щелкните правой кнопкой мыши файл External Tools. reg, сохраненный ранее, выберите пункт **Открыть с помощью**и щелкните **редактор реестра**.  
  
## <a name="writing-to-the-user-settings-store"></a>Запись в хранилище параметров пользователя  
  
1. Создайте проект VSIX с именем Усерсеттингссторикстенсион, а затем добавьте пользовательскую команду с именем Усерсеттингссторекомманд. Дополнительные сведения о создании пользовательской команды см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md) .  
  
2. В UserSettingsStoreCommand.cs добавьте следующие операторы using:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3. В Менуитемкаллбакк удалите тело метода и получите хранилище параметров пользователя следующим образом:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4. Теперь выясните, является ли Блокнот уже установленным как внешний инструмент. Чтобы определить, имеет ли параметр Тулкмд значение «Notepad», необходимо выполнить итерацию по всем внешним инструментам:  
  
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
  
5. Если Блокнот не был установлен как внешний инструмент, установите его следующим образом:  
  
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
  
6. Протестируйте код. Помните, что он добавляет Блокнот как внешний инструмент, поэтому необходимо выполнить откат реестра перед повторным запуском.  
  
7. Создайте код и начните отладку.  
  
8. В меню **Сервис** выберите команду **вызвать усерсеттингссторекомманд**. Это приведет к добавлению Блокнота в меню **Сервис** .  
  
9. Теперь вы должны увидеть Блокнот в меню Сервис/параметры, а затем щелкнуть **Блокнот** , чтобы открыть экземпляр блокнота.
