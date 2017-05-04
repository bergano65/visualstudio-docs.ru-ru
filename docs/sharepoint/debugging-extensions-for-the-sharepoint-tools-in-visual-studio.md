---
title: "Debugging Extensions for the SharePoint Tools in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, debugging extensions"
ms.assetid: 7cee8ce0-d07b-41f6-8ce1-b18e4be3b50c
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Debugging Extensions for the SharePoint Tools in Visual Studio
  Отладить расширения средств SharePoint можно в экспериментальном или обычном экземпляре Visual Studio.  При необходимости устранения неполадок поведения расширения, также можно изменить значения реестра для отображения дополнительной информации об ошибках, чтобы настроить выполнение команд SharePoint в Visual Studio.  
  
## Отладка расширений в экспериментальном экземпляре Visual Studio  
 Для защиты среды разработки Visual Studio от случайного повреждения недоверенными расширениями, пакет Visual Studio SDK предоставляет альтернативный экземпляр Visual Studio, называемый *экспериментальным экземпляром*, который можно использовать для установки и тестирования расширений.  Новые расширения разрабатываются с помощью обычного экземпляра Visual Studio, но их отладка и выполнение осуществляются в экспериментальном экземпляре.  Для получения дополнительной информации см. [Экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
 При использовании проекта VSIX для развертывания расширения, и проект VSIX в решении является автозагружаемым, при отладке решения Visual Studio автоматически установит и выполнит расширение в экспериментальном экземпляре.  Автозагружаемый проект является проектом, запуск которого происходит при отладке решения, содержащего несколько проектов.  Дополнительные сведения об использовании проекта VSIX для развертывания расширения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  Дополнительные сведения об автозагружаемых проектах см. в разделе [Практическое руководство. Назначение автозагружаемых проектов](http://msdn.microsoft.com/ru-ru/31465836-0911-48db-a5d9-e456b635e970).  
  
 Примеры отладки различных типов расширений в экспериментальном экземпляре Visual Studio см. в следующих пошаговых руководствах:  
  
-   [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
-   [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)  
  
-   [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)  
  
-   [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
-   [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## Отладка расширений в обычном экземпляре Visual Studio  
 При необходимости отладки проекта расширения в обычном экземпляре Visual Studio, его сначала следует установить в обычном экземпляре.  Затем присоедините отладчик ко второму процессу Visual Studio.  По окончании, расширение можно удалить, чтобы оно больше не занимало место на компьютере разработчика.  
  
#### Установка расширения  
  
1.  Закройте все экземпляры Visual Studio.  
  
2.  В выходную папку построения для проекта расширения, откройте файл VSIX или с помощью двойного щелчка или открыть его контекстных меню и затем выбрав команду **Открыть**.  
  
3.  В диалоговом окне **Установщик расширений Visual Studio** выберите выпуск Visual Studio, с которым требуется установить расширение, а затем нажмите кнопку **Установить**.  
  
     Visual Studio установит файлы расширения в \\*version**extension name*\\ %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions\\*author name*.  Три последние папки в этом пути создаются для расширения из элементов `Author`, `Name` и `Version` файла extension.vsixmanifest.  
  
4.  После того как Visual Studio установит расширение, нажмите кнопку **Закрыть**.  
  
#### Отладка расширения  
  
1.  Запустите Visual Studio с правами администратора и откройте проект расширения.  Следующие действия ссылаются на этот экземпляр Visual Studio как на *первый экземпляр*.  
  
2.  Запустите другой экземпляр Visual Studio с правами администратора.  Следующие действия ссылаются на этот экземпляр Visual Studio как на *второй экземпляр*.  
  
3.  Переключитесь на первый экземпляр Visual Studio.  
  
4.  В строке меню выберите **Отладка**, **Присоединение к процессу**.  
  
5.  В списке **Доступные процессы** выберите файл devenv.exe.  Этот процесс соответствует второму экземпляру Visual Studio, т. е. экземпляру, в котором будет отлаживаться расширение проекта.  
  
6.  Нажмите кнопку **Вложить**.  
  
     Visual Studio запустит проект расширения в режиме отладки.  
  
7.  Переключитесь на второй экземпляр Visual Studio.  
  
8.  Создайте новый проект SharePoint, который загружает расширение.  Например, при отладке расширения для элементов проекта определения списка, создайте проект **Определение списка**.  
  
9. Выполните действия, необходимые для проверки кода расширения.  
  
10. После окончания отладки расширения закройте второй экземпляр Visual Studio.  
  
#### Удаление расширения  
  
1.  В Visual Studio в строке меню выберите **Сервис**, **Расширения и обновления**.  
  
     Появится диалоговое окно **Расширения и обновления**.  
  
2.  В списке расширений выберите имя расширения, а затем нажмите кнопку **Удалить**.  
  
3.  В диалоговом окне, появившемся на экране, нажмите кнопку **Да**, чтобы подтвердить удаление расширения.  
  
4.  Нажмите кнопку **Перезагрузить сейчас** для завершения процесса удаления.  
  
## Отладка команд SharePoint  
 Если необходимо выполнить отладку команды SharePoint, входящей в расширение средств SharePoint, следует присоединить отладчик к процессу vssphost4.exe.  Это 64\-разрядный процесс, выполняющий команды SharePoint.  Дополнительные сведения о командах SharePoint и процессе vssphost4.exe см. в разделе [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
#### Присоединение отладчика к процессу vssphost4.exe  
  
1.  Начните отладку расширения в экспериментальном или обычном экземпляре Visual Studio, следуя инструкциям, приведенным ниже.  
  
2.  В экземпляре Visual Studio, в котором выполняется отладчик, в строке меню выберите **Отладка**, **Присоединение к процессу**.  
  
3.  В списке **Доступные процессы** выберите vssphost.exe.  
  
    > [!NOTE]  
    >  Если процесс vssphost.exe не отображается в списке, необходимо запустить vssphost4.exe в том экземпляре Visual Studio, в котором выполняется расширение.  Как правило, это происходит во время выполнения действий по подключению Visual Studio к сайту SharePoint на компьютере разработчика.  Например, Visual Studio запускает vssphost4.exe при развертывании узла подключения к сайту \(узла, отображающего URL\-адрес сайта\) в узле **Подключения SharePoint** в окне **Обозреватель серверов** или при добавлении определенных элементов проекта SharePoint, например элементов **Экземпляр списка** или **Приемник событий**, в проект SharePoint.  
  
4.  Нажмите кнопку **Вложить**.  
  
5.  В отлаживаемом экземпляре Visual Studio выполните следующие необходимые для выполнения команды шаги.  
  
## Изменение значений реестра для облегчения отладки расширений средств SharePoint  
 При отладке расширения средств SharePoint в Visual Studio можно изменять значения реестра для облегчения устранения неполадок в расширении.  Эти значения находятся в ключе HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0\\SharePointTools.  По умолчанию они не существуют.  
  
 Для облегчения устранения неполадок в расширении средств SharePoint можно создать и задайте значение EnableDiagnostics.  Это значение описывается в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|EnableDiagnostics|REG\_DWORD указывает отображаются ли диагностические сообщения в окне **Выходные данные**.<br /><br /> Чтобы отображать диагностические сообщения, присвойте значение 1.  Чтобы не отображать сообщения, присвойте значение 0 или удалите значение.<br /><br /> Чтобы записать сообщения в окно **Выходные данные** из расширения средств SharePoint, воспользуйтесь службой проекта SharePoint.  Для получения дополнительной информации см. [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).|  
  
 Если расширение содержит команду SharePoint, можно создать и задать дополнительные значения для облегчения устранения неполадок в команде.  В следующей таблице приведено описание этих значений.  
  
|Значение|Описание|  
|--------------|--------------|  
|AttachDebuggerToHostProcess|Значение REG\_DWORD определяет, отображать ли диалоговое окно, которое позволяет присоединить отладчик к процессу vssphost4.exe прямо при его запуске.  Это полезно, если отлаживаемая команда выполняется процессом vssphost.exe сразу после его запуска, и вручную присоединить отладчик невозможно из\-за недостатка времени.  Для отображения диалогового окна процесс vssphost4.exe вызывает метод <xref:System.Diagnostics.Debugger.Break%2A> при запуске.<br /><br /> Чтобы включить такой режим, задайте значение 1.  Чтобы отключить этот режим, нужно задайте значение равным 0 или удалите его.<br /><br /> Если вы установили значение равным 1, может также быть полезно увеличить значение HostProcessStartupTimeout, что позволит успеть присоединить отладчик до того момента, когда Visual Studio ожидает от процесса vssphost4.exe сигнала об успешном запуске.|  
|ChannelOperationTimeout|REG\_DWORD указывает время в секундах, в течение которого Visual Studio ожидает выполнения команды SharePoint.  Если команда не выполнена вовремя, выдается исключение <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>.<br /><br /> По умолчанию используется значение 120 секунд.|  
|HostProcessStartupTimeout|REG\_DWORD указывает время в секундах, в течение которого Visual Studio ожидает сигнала от vssphost4.exe о его успешном запуске.  Если сигнал об успешном запуске не поступил от vssphost4.exe вовремя, выдается исключение <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>.<br /><br /> По умолчанию используется значение 60 секунд.|  
|MaxReceivedMessageSize|REG\_DWORD указывает максимально допустимый размер в байтах для сообщений WCF, которыми обмениваются Visual Studio и vssphost4.exe.<br /><br /> Значение по умолчанию — 1 048 576 байтов \(1 МБ\).|  
|MaxStringContentLength|REG\_DWORD указывает максимально допустимый размер в байтах для строк, которыми обмениваются Visual Studio и vssphost4.exe.<br /><br /> Значение по умолчанию — 1 048 576 байтов \(1 МБ\).|  
  
## См. также  
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  