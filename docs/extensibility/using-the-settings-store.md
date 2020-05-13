---
title: Использование хранилища настроек (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3bbc09586f883e067e32f525a0331c1a9e253f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698521"
---
# <a name="using-the-settings-store"></a>Использование хранилища параметров
Есть два вида настроек магазинов:

- Настройки конфигурации, которые являются только для чтения Visual Studio и VSPackage настройки. Visual Studio объединяет настройки из всех известных файлов .pkgdef в этот магазин.

- Настройки пользователя, которые являются насыпи, которые являются записываемыми, например, те, которые отображаются на страницах в диалоговом поле **Options,** страницах свойств и некоторых других диалоговых коробках. Расширения Visual Studio могут использовать их для локального хранения небольших объемов данных.

  В этом пошаговом показании, как считывать данные из хранилища конфигураций. Просмотрите [запись в магазине настроек пользователя](../extensibility/writing-to-the-user-settings-store.md) для объяснения того, как писать в магазин настроек пользователя.

## <a name="creating-the-example-project"></a>Создание проекта «Пример»
 В этом разделе показано, как создать простой проект расширения с командой меню для демонстрации.

1. Каждое расширение Visual Studio начинается с проекта развертывания VSIX, который будет содержать активы расширения. Создайте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX под названием `SettingsStoreExtension`. Вы можете найти шаблон проекта VSIX в диалоге **Нового проекта** под Visual C **/ Расширяемость**.

2. Теперь добавьте пользовательский шаблон элемента команды под названием **SettingsStoreCommand.** В диалоге **Добавить новый элемент,** перейдите на **Visual C / Расширяемость** и выберите **пользовательские команды**. В поле **«Имя»** в нижней части окна измените имя файла команды на **SettingsStoreCommand.cs.** Для получения дополнительной информации о том, как создать пользовательскую команду, [см.](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Использование хранилища настроек конфигурации
 В этом разделе показано, как обнаруживать и отображать настройки конфигурации.

1. В SettingsStorageCommand.cs файле добавьте следующие директивы:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. В, `MenuItemCallback`удалить тело метода, и добавить эти строки получить настройки настройки хранения:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    Это <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> управляемый класс помощника <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> по службе.

3. Теперь узнайте, установлены ли инструменты Windows Phone. Код должен выглядеть следующим образом:

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

4. Проверьте код. Выполните сборку решения и запустите отладку.

5. В экспериментальном примере, в меню **Инструментов,** нажмите **Наймите НастройкиStoreCommand.**

    Вы должны увидеть окно сообщений, говорящий **Microsoft Windows Phone Developer Tools:** затем **True** или **False.**

   Visual Studio сохраняет хранилище настроек в системном реестре.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Использование редактора реестра для проверки настроек конфигурации

1. Откройте Regedit.exe.

2. Перейдите на HKEY_CURRENT_USER программное обеспечение»Microsoft-VisualStudio »14.0Exp_Config»- Установленныепродукты\\.

    > [!NOTE]
    > Убедитесь, что вы смотрите на ключ, который содержит «14.0Exp_Config», а не «14.0_Config\\. При запуске экспериментального экземпляра Visual Studio настройки конфигурации находятся в реестре улья "14.0Exp_Config".

3. Расширьте узлы «Установленные продукты». Если сообщение в предыдущих шагах **Microsoft Windows Phone Developer Tools Installed: True**, то «Установленные продукты» должны содержать узло инструментов для разработчиков Microsoft Windows Phone. Если сообщение **Microsoft Windows Phone Developer Tools Installed: False**, то «Установленные продукты» не должны содержать узел инструментов для разработчиков Microsoft Windows Phone.
