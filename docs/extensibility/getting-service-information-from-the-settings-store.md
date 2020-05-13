---
title: Получение информации об обслуживании из магазина настроек (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b15d5c9f122ca66d21940b9998969b0d39d1a74d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711376"
---
# <a name="get-service-information-from-the-settings-store"></a>Получить информацию об услугах в магазине настроек
Вы можете использовать хранилище настроек, чтобы найти все доступные службы или определить, установлена ли та или иная служба. Вы должны знать тип класса обслуживания.

## <a name="to-list-the-available-services"></a>Перечислить доступные услуги

1. Создайте проект VSIX с `FindServicesExtension` именем, `FindServicesCommand`а затем добавьте пользовательскую команду с именем. Для получения дополнительной информации о том, как создать пользовательскую команду, [см.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. В *FindServicesCommand.cs*добавьте следующие директивы:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Получите хранилище настроек конфигурации, а затем найдите подколлекцию под названием Услуги. Эта коллекция включает в себя все доступные услуги. В `MenuItemCommand` методе удалите существующий код и замените его следующим:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string message = "Available services:\n";
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");
        int n = 0;
        foreach (string service in collection)
        {
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";
        }

        MessageBox.Show(message);
    }
    ```

4. Выполните сборку решения и запустите отладку. Появляется экспериментальный экземпляр.

5. В экспериментальном примере, в меню **Tools,** нажмите **Найдите FindServicesCommand.**

     Вы должны увидеть окно сообщения, перечисляя все службы.

     Для проверки этих настроек можно использовать редактор реестра.

## <a name="find-a-specific-service"></a>Найти конкретную услугу
 Вы также можете <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> использовать метод для определения того, установлена ли та или иная служба. Вы должны знать тип класса обслуживания.

1. В MenuItemCallback проекта, созданного в предыдущей процедуре, поиск `Services` настройки настройки магазина для коллекции, которая имеет подколлекцию, названную GUID службы. В этом случае мы будем искать службу помощи.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);
        string message = "Help Service Available: " + hasHelpService;

        MessageBox.Show(message);
    }
    ```

2. Выполните сборку решения и запустите отладку.

3. В экспериментальном примере, в меню **Tools,** нажмите **Найдите FindServicesCommand.**

     Вы должны увидеть сообщение с текстом **Справка Служба Доступна:** затем **True** или **False**. Для проверки этой настройки можно использовать редактор реестра, как показано на предыдущих этапах.
