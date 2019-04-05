---
title: Получение сведений о службе из Store параметры | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f180642cf40c28bafcaf16eb68c36fc157914f11
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989871"
---
# <a name="getting-service-information-from-the-settings-store"></a>Получение сведений о службе из хранилища параметров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Параметры хранилища можно использовать для поиска всех доступных служб или требуется определить, установлена ли определенная служба. Необходимо знать тип класса службы.  
  
### <a name="to-list-the-available-services"></a>Чтобы получить список доступных служб  
  
1.  Создайте проект VSIX с именем FindServicesExtension, а затем добавьте пользовательскую команду с именем FindServicesCommand. Дополнительные сведения о том, как создать настраиваемую команду см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  В FindServicesCommand.cs, добавьте следующие операторы using:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  Получите хранилище параметров конфигурации, а затем найдите вложенную коллекцию, с именем службы. Эта коллекция содержит все доступные службы. В методе MenuItemCommand удалите существующий код и замените его следующим кодом:  
  
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
  
5.  В экспериментальном экземпляре на **средства** меню, щелкните **вызвать FindServicesCommand**.  
  
     Вы должны увидеть окно сообщения со списком всех служб.  
  
     Чтобы проверить эти параметры, можно использовать редактор реестра.  
  
## <a name="finding-a-specific-service"></a>Поиск определенной службы  
 Можно также использовать <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> метод, чтобы определить, установлена ли определенная служба. Необходимо знать тип класса службы.  
  
1.  В MenuItemCallback проекта, созданного в предыдущей процедуре, найдите в магазине параметры конфигурации `Services` коллекции, которая содержит вложенную коллекцию, с именем, идентификатор GUID службы. В этом случае мы будем искать службу справки.  
  
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
  
3.  В экспериментальном экземпляре на **средства** меню, щелкните **вызвать FindServicesCommand**.  
  
     Вы увидите сообщение с текстом **помочь доступные службы:** следуют **True** или **False**. Чтобы проверить этот параметр, можно использовать редактор реестра, как показано в предыдущих шагах.
