---
title: Практическое руководство. Создание команды SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 49d253b63b682d81903003d6bdd148922989f274
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082325"
---
# <a name="how-to-create-a-sharepoint-command"></a>Практическое руководство. Создание команды SharePoint
  Если вы хотите использовать серверную объектную модель в расширения инструментов SharePoint, необходимо создать пользовательский *команды SharePoint* для вызова API. Команда SharePoint определяется в сборке, которая может напрямую вызывать серверную объектную модель.

 Дополнительные сведения о назначении команд SharePoint см. в разделе [вызова объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-create-a-sharepoint-command"></a>Создание команды SharePoint

1. Создайте проект библиотеки классов, который имеет следующую конфигурацию:

    - Предназначенный для .NET Framework 3.5. Дополнительные сведения о выборе целевой платформы, см. в разделе [как: определить целевую версию .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

    - Целевая платформа AnyCPU или x64 платформы. По умолчанию целевая платформа для проектов библиотек классов — AnyCPU. Дополнительные сведения о выборе целевой платформы см. в разделе [как: настроить целевые платформы в проектах](../ide/how-to-configure-projects-to-target-platforms.md).

    > [!NOTE]
    >  Команды SharePoint не может реализовать в том же проекте, который определяет расширение инструментов SharePoint, так как команды SharePoint предназначены для целевой платформы .NET Framework 3.5 и SharePoint средства расширения [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Необходимо определить команды SharePoint, используемых модулем в отдельном проекте. Дополнительные сведения см. в разделе [развертывания расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

2. Добавьте ссылки на следующие сборки:

    - Microsoft.VisualStudio.SharePoint.Commands

    - Microsoft.SharePoint

3. В класс в проекте создайте метод, который определяет команду SharePoint. Этот метод должен соответствовать следующим правилам:

    - Он может иметь один или два параметра.

         Первый параметр должен быть <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> объекта. Этот объект предоставляет Microsoft.SharePoint.SPSite или Microsoft.SharePoint.SPWeb, в котором выполняется команда. Он также предоставляет <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> объект, который может использоваться для записи сообщений в **вывода** окна или **список ошибок** окно в Visual Studio.

         Второй параметр может быть типом по своему усмотрению, но этот параметр является необязательным. Этот параметр можно добавить команду SharePoint, если необходимо передать данные из расширения средств SharePoint в команду.

    - Он может иметь возвращаемое значение, но это необязательно.

    - Второй параметр и возвращаемое значение должно быть типом, который может быть сериализован с Windows Communication Foundation (WCF). Дополнительные сведения см. в разделе [Types Supported by the Data Contract Serializer](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) и [с помощью класса XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).

    - Метод может быть любой уровень (**открытый**, **внутренней**, или **частного**), и может быть статическим или статическим.

4. Применить <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> методу. Этот атрибут задает уникальный идентификатор для команды; Этот идентификатор не совпадает с именем метода.

     При вызове команды из расширения средств SharePoint необходимо указать тот же уникальный идентификатор. Дополнительные сведения см. в разделе [Как Выполнение команды SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md).

## <a name="example"></a>Пример
 В следующем примере кода демонстрируется команда SharePoint с идентификатором `Contoso.Commands.UpgradeSolution`. Эта команда использует интерфейсы API в серверной объектной модели для обновления до развернутого решения.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 Помимо явного первого <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> параметр, эта команда также имеет параметр пользовательскую строку, содержащую полный путь к WSP-файла, которое обновляется на сайте SharePoint. Этот код в контексте большего примера, см. в разделе [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="compiling-the-code"></a>Компиляция кода
 В этом примере требуются ссылки на следующие сборки:

- Microsoft.VisualStudio.SharePoint.Commands

- Microsoft.SharePoint

## <a name="deploying-the-command"></a>Развертывание команды
 Чтобы развернуть команды, включите ее сборку в том же [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] расширения (*vsix*) пакета с помощью сборки модуля, который использует команду. Необходимо также добавить запись для сборки команды в файл extension.vsixmanifest. Дополнительные сведения см. в разделе [развертывания расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также
- [Вызов объектных моделей SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Практическое руководство. Выполнение команды SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Пошаговое руководство: Расширения обозревателя сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
