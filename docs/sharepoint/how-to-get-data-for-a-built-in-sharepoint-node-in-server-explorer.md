---
title: Как выполнить Получение данных для встроенного узла SharePoint в обозревателе серверов | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e9ef30de63789072f021aaded87dd5e9c8071637
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898977"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Как выполнить Получение данных для встроенного узла SharePoint в обозревателе серверов
  Для каждого узла SharePoint, встроенного в **обозревателя серверов**, можно получить данные по указанному компоненту SharePoint, которую представляет узел. Дополнительные сведения см. в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано получение данных по указанному списку SharePoint, который узле списка в **обозревателя серверов**. По умолчанию узлы списка содержат **просмотреть в браузере** пункт контекстного меню, которую можно щелкнуть, чтобы открыть список в веб-браузере. Этот пример расширяет список узлов, добавив **представления в Visual Studio** пункт контекстного меню, открывшемся списки непосредственно в Visual Studio. Код обращается к данным списка для узла, чтобы получить URL-адрес списка, чтобы открыть в Visual Studio.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]  
  
 В этом примере используется служба проекта SharePoint для получения <xref:EnvDTE.DTE> объект, который используется для открытия списков в Visual Studio. Дополнительные сведения о службе проекта SharePoint, см. в разделе [использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Дополнительные сведения об основных задачах для создания расширения узла SharePoint см. в разделе [как: Расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="compile-the-code"></a>Компиляция кода  
 В этом примере требуются ссылки на следующие сборки:  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Развертывание расширения  
 Для развертывания **обозревателя серверов** расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывания расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также
 [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Практическое руководство. Расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
