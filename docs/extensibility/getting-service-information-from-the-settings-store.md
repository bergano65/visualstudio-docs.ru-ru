---
title: Получение сведений о службе из хранилища настроек | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11731e36517ae6245dddd1ebdd3b002fb3c37391
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="getting-service-information-from-the-settings-store"></a>Получение сведений о службе из хранилища настроек
Параметры хранилища можно использовать для поиска всех доступных служб или требуется определить, установлена ли определенная служба. Необходимо знать тип класса службы.  
  
### <a name="to-list-the-available-services"></a>Чтобы вывести список доступных служб  
  
1.  Создайте проект VSIX с именем FindServicesExtension, а затем добавьте пользовательскую команду с именем FindServicesCommand. Дополнительные сведения о том, как создать настраиваемую команду см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  В FindServicesCommand.cs, добавьте следующие операторы using:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  Получение параметров хранилища конфигурации, а затем найти вложенной коллекцией, с именем службы. Эта коллекция содержит список доступных служб. В методе MenuItemCommand удалите существующий код и замените его следующим кодом:  
  
    ```  
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
  
4.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
5.  В экспериментальном экземпляре на **средства** меню, нажмите кнопку **FindServicesCommand вызова**.  
  
     Появится окно сообщения со списком всех служб.  
  
     Чтобы проверить эти параметры, можно использовать редактор реестра.  
  
## <a name="finding-a-specific-service"></a>Поиск определенной службы  
 Можно также использовать <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> метод, чтобы определить, установлена ли определенная служба. Необходимо знать тип класса службы.  
  
1.  В MenuItemCallback проект, созданный в предыдущей процедуре, выполните поиск в магазине параметры конфигурации для `Services` коллекции с вложенной коллекцией, названный GUID службы. В этом случае будет искать службы справки.  
  
    ```  
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
  
2.  Выполните сборку решения и запустите отладку.  
  
3.  В экспериментальном экземпляре на **средства** меню, нажмите кнопку **FindServicesCommand вызова**.  
  
     Появится сообщение с текстом **справки доступны службы:** следуют **True** или **False**. Чтобы проверить этот параметр, можно использовать редактор реестра, как показано в предыдущих шагах.