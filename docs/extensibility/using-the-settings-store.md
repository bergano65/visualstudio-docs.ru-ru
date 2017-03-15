---
title: "С помощью параметров магазина | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Хранилище настроек с помощью"
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# С помощью параметров магазина
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Существует два типа параметров хранилищ:  
  
-   Параметры конфигурации, которые являются только для чтения параметров Visual Studio и VSPackage. Visual Studio объединяет параметры из всех известных .pkgdef файлы в это хранилище.  
  
-   Параметры пользователя, а для записи параметров, например те, которые отображаются на страницах в **Параметры** диалоговое окно страницы свойств и некоторых других диалоговых окон. Расширения Visual Studio может использовать их для локального хранения небольших объемов данных.  
  
 В этом пошаговом руководстве показано, как считывать данные из хранилища параметров конфигурации. В разделе [Запись в хранилище настроек пользователя](../extensibility/writing-to-the-user-settings-store.md) Объяснение того, как запись в хранилище настроек пользователя.  
  
## Создание примера проекта  
 В этом разделе показано, как создать проект простое расширение с помощью команды меню для демонстрационных целей.  
  
1.  Все расширения Visual Studio начинается с развертывания проект VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `SettingsStoreExtension`. Можно найти шаблон проекта VSIX в **Новый проект** диалоговом окне под **Visual C\# и расширяемость**.  
  
2.  Теперь добавьте пользовательскую команду шаблон элемента с именем **SettingsStoreCommand**. В **Добавление нового элемента** диалоговое окно, последовательно выберите пункты **Visual C\# и расширяемость** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя файла команд для **SettingsStoreCommand.cs**. Дополнительные сведения о создании пользовательской команды см. [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## С помощью хранилища параметров конфигурации  
 В этом разделе показано, как обнаруживать и отображает параметры конфигурации.  
  
1.  В файле SettingsStorageCommand.cs добавьте следующие операторы using:  
  
    ```  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings; using System.Windows.Forms;  
    ```  
  
2.  В `MenuItemCallback`, удалите тела метода и добавьте эти строки получения хранилища параметров конфигурации:  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> Превышает управляемый вспомогательный класс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> службы.  
  
3.  Теперь Узнайте, установлены ли средства Windows Phone. Код должен выглядеть следующим образом:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools"); string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled; MessageBox.Show(message); }  
    ```  
  
4.  Проверьте код. Выполните сборку решения и запустите отладку.  
  
5.  В экспериментальном экземпляре на **средства** меню, щелкните **вызова SettingsStoreCommand**.  
  
     Вы должны увидеть сообщение поле **средств разработчика Windows Phone:**  следуют **True** или **False**.  
  
 Visual Studio сохраняет хранилища параметров в системном реестре.  
  
#### Чтобы проверить параметры конфигурации с помощью редактора реестра  
  
1.  Откройте Regedit.exe.  
  
2.  Перейдите к HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0Exp\_Config\\InstalledProducts\\.  
  
    > [!NOTE]
    >  Убедитесь, что вы находитесь на ключ, который содержит \\14.0Exp\_Config\\ и не \\14.0\_Config\\. При запуске экспериментальном экземпляре Visual Studio, параметры конфигурации будут в кусте реестра «14.0Exp\_Config».  
  
3.  Разверните узел \\Installed Products\\. Если сообщение в предыдущих шагах **установлен по средства разработчика Microsoft Windows Phone: True**, то \\Installed Products\\ должен содержать узел средств разработчика Windows Phone. Если сообщение **установлен по средства разработчика Microsoft Windows Phone: False**, а затем \\Installed Products\\ не должны содержать узел средств разработчика Windows Phone.