---
title: Получение сведений о службе из хранилища параметров | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfe754203ae9b4e951de5beef8cd829f9d7716bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204309"
---
# <a name="getting-service-information-from-the-settings-store"></a>Получение сведений о службе из хранилища параметров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью хранилища параметров можно найти все доступные службы или определить, установлена ли определенная служба. Необходимо иметь представление о типе класса службы.  
  
### <a name="to-list-the-available-services"></a>Перечисление доступных служб  
  
1. Создайте проект VSIX с именем Финдсервицесекстенсион, а затем добавьте пользовательскую команду с именем Финдсервицескомманд. Дополнительные сведения о создании пользовательской команды см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md) .  
  
2. В FindServicesCommand.cs добавьте следующие операторы using:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3. Получите хранилище параметров конфигурации, а затем найдите вложенную коллекцию с именем Services. Эта коллекция включает все доступные службы. В методе Менуитемкомманд удалите существующий код и замените его следующим:  
  
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
  
4. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
5. В экспериментальном экземпляре в меню **Сервис** выберите команду **вызвать финдсервицескомманд**.  
  
     Должно отобразиться окно сообщения со списком всех служб.  
  
     Чтобы проверить эти параметры, можно использовать редактор реестра.  
  
## <a name="finding-a-specific-service"></a>Поиск конкретной службы  
 Можно также использовать метод, <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> чтобы определить, установлена ли определенная служба. Необходимо иметь представление о типе класса службы.  
  
1. В Менуитемкаллбакк проекта, созданного в предыдущей процедуре, выполните поиск в хранилище параметров конфигурации для `Services` коллекции, которая содержит подколлекцию с именем по идентификатору GUID службы. В этом случае мы будем искать службу справки.  
  
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
  
2. Выполните сборку решения и запустите отладку.  
  
3. В экспериментальном экземпляре в меню **Сервис** выберите команду **вызвать финдсервицескомманд**.  
  
     Должно отобразиться сообщение со **справочной службой "текст справки":**  , за которым следует **значение true** или **false**. Чтобы проверить этот параметр, можно использовать редактор реестра, как показано на предыдущих шагах.
