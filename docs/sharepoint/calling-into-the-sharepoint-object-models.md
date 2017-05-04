---
title: "Calling into the SharePoint Object Models | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint development in Visual Studio, server object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: 99934f9e-901e-464e-ac8c-22c6c86440f4
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Calling into the SharePoint Object Models
  При создании расширений для средств SharePoint в Visual Studio, можно вызвать API SharePoint выполнять определенные задачи.  Например, при создании пользовательского шага развертывания проектов SharePoint может возникнуть необходимость вызвать API SharePoint, чтобы выполнить некоторые задачи по развертыванию решений.  
  
 В [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] и [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] реализуются две различные объектные модели, которые можно использовать в расширениях средств SharePoint: серверная объектная модель и клиентская объектная модель.  У каждой из объектных моделей имеются свои преимущества и недостатки в контексте расширений средств SharePoint.  
  
 Общие сведения об объектных моделях SharePoint см. в разделе [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## Использование в проектах расширений клиентской объектной модели  
 При разработке расширения для средств SharePoint клиентскую объектную модель можно использовать в проекте наравне с любым другим набором управляемых интерфейсов API.  В проект можно добавлять ссылки на сборки клиентской объектной модели, либо можно вызывать API в клиентской объектной модели непосредственно из кода.  
  
 Впрочем, у клиентской объектной модели имеется два недостатка в контексте расширений средств SharePoint.  
  
-   Клиентская объектная модель является только подмножеством серверной объектной модели.  Если требуется использовать функции SharePoint, которые не доступны в клиентской объектной модели, следует использовать серверную объектную модель.  
  
-   Несмотря на то что клиентская объектная модель должна работать в расширениях средств SharePoint в большинстве случаев, возможны ситуации, при которых вызов клиентской объектной модели будет работать некорректно.  Клиентская объектная модель предназначена для использования в клиентских приложениях для вызова сайтов SharePoint на удаленном сервере или ферме.  Средства SharePoint Visual Studio работают только с локальным экземпляром SharePoint, установленным на компьютере разработчика.  Поэтому при использовании клиентской объектной модели в расширении средств SharePoint происходит вызов сайта SharePoint на локальном компьютере, что не является правильным использованием клиентской объектной модели.  
  
 Пошаговое руководство, которое демонстрирует, как использовать клиентскую объектную модель в расширении средств SharePoint в Visual Studio [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md) см. в разделе.  
  
## Использование в проектах расширений серверной объектной модели  
 Серверная объектная модель является надмножеством клиентской объектной модели.  При использовании серверной объектной модели можно программным образом использовать все функции, доступные в [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] и [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)].  
  
 Расширения средств SharePoint могут использовать API в серверной объектной модели, но они не могут вызывать API напрямую.  Серверную объектную модель можно вызывать только из 64\-разрядных процессов, предназначенных для версии .NET Framework 3.5.  Средства расширения SharePoint требуют [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и работают в 32\-разрядном процессе Visual Studio.  Это позволяет избежать использования в расширениях средств SharePoint прямых ссылок на сборки серверной объектной модели SharePoint.  
  
 Если в расширениях средств SharePoint требуется использовать серверную объектную модель, необходимо создать для вызова API настраиваемую *команду SharePoint*.  Команда SharePoint определяется в дополнительной сборке, которая может напрямую вызывать серверную объектную модель.  В проекте расширения команда SharePoint вызывается опосредованно через метод ExecuteCommand объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  
  
 Дополнительные сведения о создании и использовании команд SharePoint см. в разделах [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md) и [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md).  Дополнительные сведения о развертывании команд SharePoint см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Пошаговые руководства по созданию и использованию команд SharePoint см. в разделах [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) и [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### Принципы выполнения команд SharePoint  
 Сборки, определяющие команды SharePoint, загружаются в 64\-разрядный хост\-процесс с именем vssphost4.exe.  После вызова команды SharePoint в расширении средств SharePoint команда выполняется в процессе vssphost4.exe, а не 32\-разрядном процессе Visual Studio \(devenv.exe\).  Задавая значения в реестре, можно управлять некоторыми принципами выполнения команд SharePoint.  Дополнительные сведения см. в разделе [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  