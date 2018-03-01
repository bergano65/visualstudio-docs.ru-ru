---
title: "С помощью параметров хранилища | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ecb7cf4a40793116159bd2ff8292f0303e3cc46f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-settings-store"></a>С помощью параметров хранилища
Существует два типа параметров хранилищ:  
  
-   Параметры конфигурации, которые являются только для чтения параметров Visual Studio и пакет VSPackage. Visual Studio осуществляет слияние параметров из всех известных .pkgdef файлов это хранилище.  
  
-   Параметры пользователя, — параметры, доступные для записи, например те, которые отображаются на страницах в **параметры** диалоговое окно страниц свойств и некоторых других диалоговых окон. Расширения Visual Studio может использовать эти данные для локального хранения небольших объемов данных.  
  
 В этом пошаговом руководстве показано, как считывать данные из хранилища параметр конфигурации. В разделе [записи в хранилище настроек пользователя](../extensibility/writing-to-the-user-settings-store.md) объяснение того, как для записи в хранилище настроек пользователя.  
  
## <a name="creating-the-example-project"></a>Создание примера проекта  
 В этом разделе показано создание простого расширения проекта с помощью команды меню для демонстрационных целей.  
  
1.  Все расширения Visual Studio начинается с проект развертывания VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `SettingsStoreExtension`. Шаблон проекта VSIX в можно найти **новый проект** диалогового окна в разделе **Visual C# / Extensibility**.  
  
2.  Теперь добавьте пользовательскую команду шаблон элемента с именем **SettingsStoreCommand**. В **Добавление нового элемента** диалоговое окно, перейдите на **Visual C# / Extensibility** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя файла команд для **SettingsStoreCommand.cs**. Дополнительные сведения о том, как создать настраиваемую команду см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>С помощью параметров конфигурации хранилища  
 В этом разделе показано, как для обнаружения и отображения параметров конфигурации.  
  
1.  В файле SettingsStorageCommand.cs добавьте следующие операторы using:  
  
    ```  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
2.  В `MenuItemCallback`, удалить тело метода и добавьте эти строки получить хранилище параметров конфигурации:  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
    SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> Превышает управляемый вспомогательный класс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> службы.  
  
3.  Теперь Узнайте, установлены ли средства Windows Phone. Код должен выглядеть следующим образом:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
        string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  Тестирование кода. Выполните сборку решения и запустите отладку.  
  
5.  В экспериментальном экземпляре на **средства** меню, нажмите кнопку **SettingsStoreCommand вызова**.  
  
     Должно появиться сообщение поле **инструменты разработчика Microsoft Windows Phone:** следуют **True** или **False**.  
  
 Visual Studio сохраняет параметры хранилища в системном реестре.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Чтобы проверить параметры конфигурации с помощью редактора реестра  
  
1.  Откройте Regedit.exe.  
  
2.  Перейдите к HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.  
  
    > [!NOTE]
    >  Убедитесь, что вы находитесь на ключ, который содержит \14.0Exp_Config\ и не \14.0_Config\\. При запуске экспериментальный экземпляр Visual Studio, параметры конфигурации находятся в кусте реестра «14.0Exp_Config».  
  
3.  Разверните узел \Installed Products\. Если сообщение в предыдущих шагах **установлен по инструменты разработчика Microsoft Windows Phone: True**, то \Installed Products\ должен содержать узел Microsoft Windows Phone Developer Tools. Если сообщение **установлен по инструменты разработчика Microsoft Windows Phone: False**, а затем \Installed Products\ не должно содержать узел Microsoft Windows Phone Developer Tools.