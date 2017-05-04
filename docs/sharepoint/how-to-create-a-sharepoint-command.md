---
title: "How to: Create a SharePoint Command | Microsoft Docs"
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
  - "SharePoint commands [SharePoint development in Visual Studio], creating"
ms.assetid: e1fda8f0-eae1-4278-91c1-19a5e1fc327f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# How to: Create a SharePoint Command
  Если в расширениях средств SharePoint требуется использовать серверную объектную модель, необходимо создать для вызова API настраиваемую *команду SharePoint*.  Команда SharePoint определяется в сборке, которая может напрямую вызывать серверную объектную модель.  
  
 Дополнительные сведения о командах SharePoint см. в разделе [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### Создание команды SharePoint  
  
1.  Создайте проект библиотеки классов с приведенной ниже конфигурацией.  
  
    -   Предназначенный для платформы .NET Framework 3.5.  Дополнительные сведения о выборе целевой платформы см. в разделе [Практическое руководство. Определение целевой версии .NET Framework](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md).  
  
    -   Предназначенный для AnyCPU или платформы x64.  По умолчанию целевой платформой проектов библиотек классов является AnyCPU.  Дополнительные сведения о выборе целевой платформы см. в разделе [NIB: How to: Optimize an Application for a Specific CPU Type](http://msdn.microsoft.com/ru-ru/294a75d2-4279-4b72-8298-2bea05be907a).  
  
    > [!NOTE]  
    >  Команду SharePoint нельзя реализовать в том же проекта, в котором определяется расширение средств SharePoint, поскольку целевой платформой команд SharePoint является .NET Framework 3.5, а расширения средств SharePoint предназначены для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  Следует определить все команды SharePoint, используемые расширением в отдельном проекте.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
2.  Добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  Создайте в классе проекта метод, определяющий команду SharePoint.  Этот метод должен соответствовать следующим требованиям.  
  
    -   У него может быть один или два параметра.  
  
         Первым параметром должен быть объект <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>.  Этот объект предоставляет класс Microsoft.SharePoint.SPSite или Microsoft.SharePoint.SPWeb, в котором выполняется команда.  Также он предоставляет объект <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger>, который можно использовать для записи сообщений в окно **Выходные данные** или окно **Список ошибок** в Visual Studio.  
  
         Тип второго параметра пользователь может выбрать на свое усмотрение, он этот параметр не обязательный.  Этот параметр можно добавить в команду SharePoint при необходимости передать в нее данные из расширения средств SharePoint.  
  
    -   У него может быть возвращаемое значение, но оно необязательное.  
  
    -   Второй параметр и возвращаемое значение должны относиться к типу, который можно сериализовать средствами Windows Communication Foundation \(WCF\).  Дополнительные сведения см. в разделах [Типы, поддерживаемые сериализатором контракта данных](../Topic/Types%20Supported%20by%20the%20Data%20Contract%20Serializer.md) и [Использование класса XmlSerializer](../Topic/Using%20the%20XmlSerializer%20Class.md).  
  
    -   У метода может быть любой уровень видимости \(**public**, **internal** или **private**\), кроме того, он может быть статическим или не статическим.  
  
4.  Примените атрибут <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> к методу.  Этот атрибут задает уникальный идентификатор команды; данный идентификатор не обязательно должен совпадать с именем метода.  
  
     Такой же уникальный идентификатор нужно задать при вызове команды из расширения средств SharePoint.  Дополнительные сведения см. в разделе [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md).  
  
## Пример  
 В следующем примере кода показана команда SharePoint с идентификатором `Contoso.Commands.UpgradeSolution`.  Эта команда использует интерфейсы API в серверной объектной модели для обновления до развертываемого решения.  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#5)]  
  
 Кроме явного первого параметра <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> у этой команды также есть настраиваемый параметр строкового типа, содержащий полный путь к WSP\-файлу, который обновляется до сайта SharePoint.  Данный код в контексте полного примера см. в раздел [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## Развертывание команды  
 Для развертывания команды включите ее сборку в один пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) со сборкой развертывания, использующей эту команду.  Кроме того следует также добавить в VSIXMANIFEST\-файл расширения запись для сборки команды.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  