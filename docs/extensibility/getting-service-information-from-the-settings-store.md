---
title: "Получение сведений о службе из хранилища параметров | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Получение сведений о службе из хранилища параметров
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Хранилище настроек можно использовать для поиска всех доступных служб или чтобы определить, установлена ли определенная служба. Необходимо знать тип класса службы.  
  
### Чтобы получить список доступных служб  
  
1.  Создайте проект VSIX с именем FindServicesExtension, а затем добавьте пользовательскую команду с именем FindServicesCommand. Дополнительные сведения о создании пользовательской команды см. [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  В FindServicesCommand.cs, добавьте следующие операторы using:  
  
    ```vb  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings; using System.Windows.Forms;  
    ```  
  
3.  Получение хранилища параметров конфигурации, а затем найдите подколлекции с именем службы. Эта коллекция содержит список доступных служб. В методе MenuItemCommand удалите существующий код и замените его следующим кодом:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); string message = "Available services:\n"; IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services"); int n = 0; foreach (string service in collection) { message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n"; } MessageBox.Show(message); }  
    ```  
  
4.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
5.  В экспериментальном экземпляре на **средства** меню, щелкните **вызова FindServicesCommand**.  
  
     Появится окно сообщения со списком всех служб.  
  
     Чтобы проверить эти параметры, можно использовать редактор реестра.  
  
## Поиск определенной службы  
 Можно также использовать <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> метод, чтобы определить, установлена ли определенная служба. Необходимо знать тип класса службы.  
  
1.  Хранилище параметров конфигурации для поиска MenuItemCallback проекта, созданного в предыдущей процедуре, `Services` коллекции с вложенной коллекцией, названный GUID службы. В этом случае будет выполнен поиск справочной службы.  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper(); bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID); string message = "Help Service Available: " + hasHelpService; MessageBox.Show(message); }  
    ```  
  
2.  Выполните сборку решения и запустите отладку.  
  
3.  В экспериментальном экземпляре на **средства** меню, щелкните **вызова FindServicesCommand**.  
  
     Должно появиться сообщение с текстом **доступность справки службы:**  следуют **True** или **False**. Чтобы проверить этот параметр, можно использовать редактор реестра, как показано на предыдущих этапах.