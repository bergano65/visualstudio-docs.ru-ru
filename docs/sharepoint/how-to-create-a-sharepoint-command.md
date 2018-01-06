---
title: "Как: создание команды SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint commands [SharePoint development in Visual Studio], creating
ms.assetid: e1fda8f0-eae1-4278-91c1-19a5e1fc327f
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 42aa28637bc513865f96c0b88d2ca7c4dd726c5c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-sharepoint-command"></a>Практическое руководство. Создание команды SharePoint
  Если вы хотите использовать в расширении инструментов SharePoint в серверную объектную модель, необходимо создать пользовательский *команда SharePoint* для вызова API. Команда SharePoint определяется в сборке, которая может напрямую вызывать серверную объектную модель.  
  
 Дополнительные сведения о назначении команд SharePoint см. в разделе [вызова объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-create-a-sharepoint-command"></a>Создание команды SharePoint  
  
1.  Создайте проект библиотеки классов, которая имеет следующую конфигурацию:  
  
    -   Предназначен для платформы .NET Framework 3.5. Дополнительные сведения о выборе целевой платформы см. в разделе [как: целевой версии платформы .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
    -   Обращается AnyCPU или x64 платформы. По умолчанию целевая платформа для проектов библиотек классов является AnyCPU. Дополнительные сведения о выборе целевой платформы см. в разделе [как: Настройка проекта для конкретной платформы](../ide/how-to-configure-projects-to-target-platforms.md).  
  
    > [!NOTE]  
    >  Нельзя реализовать команда SharePoint в том же проекте, который определяет расширения инструментов SharePoint, так как команды SharePoint указывают целевого расширения средств .NET Framework 3.5 и SharePoint [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Необходимо определить все команды SharePoint, используемые расширением в отдельном проекте. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
2.  Добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  В классе в проекте создайте метод, определяющий команду SharePoint. Этот метод должен соответствовать следующим правилам:  
  
    -   Он может иметь один или два параметра.  
  
         Первый параметр должен быть <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> объекта. Этот объект предоставляет Microsoft.SharePoint.SPSite или Microsoft.SharePoint.SPWeb, в котором выполняется команда. Он также предоставляет <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> объект, который может использоваться для записи сообщений в **вывода** окна или **список ошибок** окна в Visual Studio.  
  
         Второй параметр может иметь любой тип, но этот параметр является необязательным. Этот параметр можно добавить команду SharePoint, если нужно передать данные из расширения инструментов SharePoint в команду.  
  
    -   Он может иметь значение, возвращаемое, но это не обязательно.  
  
    -   Второй параметр и возвращаемое значение должно быть типом, который может быть сериализован, Windows Communication Foundation (WCF). Дополнительные сведения см. в разделе [типы, поддерживаемые сериализатором контракта данных](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) и [с помощью класса XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).  
  
    -   Метод может быть любой уровень (**открытый**, **внутренней**, или **закрытый**), и может быть статическим или не статическими.  
  
4.  Применить <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> методу. Этот атрибут задает уникальный идентификатор для команды; Этот идентификатор не имеет должно соответствовать имени метода.  
  
     При вызове команды из расширения инструментов SharePoint необходимо указать такой же уникальный идентификатор. Дополнительные сведения см. в разделе [как: выполнение команды SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется команда SharePoint с идентификатором `Contoso.Commands.UpgradeSolution`. Эта команда использует интерфейсы API в серверной объектной модели для обновления до развертываемого решения.  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]  
  
 Кроме явного первого <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> параметра, эта команда также имеет параметр пользовательская строка, содержащая полный путь WSP-файла, которая обновляется на сайте SharePoint. Этот код в контексте полного примера см. в разделе [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## <a name="deploying-the-command"></a>Развертывание команды  
 Чтобы развернуть команды, включите ее сборку в том же [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) со сборкой, использующей эту команду. Необходимо также добавить запись для сборки команды в файл extension.vsixmanifest. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Обращение к объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Как: выполнение команды SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Пошаговое руководство. Расширение обозревателя сервера, так чтобы в нем отображались веб-части](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  