---
title: "Расширение узла подключений SharePoint в обозревателе серверов | Документы Microsoft"
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
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 879d34828e4619ac9a538f9db7cf1acef7b830b0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="extending-the-sharepoint-connections-node-in-server-explorer"></a>Расширение узла подключений SharePoint в обозревателе сервера
  В Visual Studio можно подключиться к локальным сайтам SharePoint на компьютере разработчика с помощью **подключения SharePoint** узел в**обозревателя серверов** окна. Этот узел содержит многие компоненты локальных сайтов SharePoint в виде иерархического дерева. Например можно просмотреть списки, библиотеки документов и типы содержимого на локальных сайтах. Дополнительные сведения об использовании **обозревателя серверов** для подключения к локальным сайтам SharePoint, в разделе [просмотра SharePoint подключения с помощью сервера обозревателя](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 Вы можете расширить **подключения SharePoint** узла, создав расширения для существующих узлов или создав пользовательский тип узла и добавив его в иерархию узлов.  
  
## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Задачи для расширение узла подключений SharePoint  
 Чтобы расширить существующий узел, создать расширение Visual Studio, который реализует <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> интерфейса. При расширении узла можно добавить функциональные возможности на узел, например собственные элементы контекстного меню или пользовательские свойства. Дополнительные сведения см. в разделе [как: расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Чтобы создать пользовательский тип узла, создайте расширение Visual Studio, который реализует <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> интерфейса. Создать пользовательский узел, если требуется отображать компоненты сайтов SharePoint, которые не отображаются в **обозревателя серверов** по умолчанию. Например **обозревателя серверов** не должно отображаться галерею веб-частей на сайт SharePoint, по умолчанию, но можно добавить пользовательский узел такому же принципу. Дополнительные сведения см. в разделе [как: добавить пользовательского узла SharePoint в обозревателе серверов](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) и [Пошаговое руководство: расширение обозревателя серверов для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="adding-custom-properties-to-nodes"></a>Добавление пользовательских свойств в узлы  
 При расширении узла, или создать пользовательский тип узла, можно добавить пользовательские свойства на узел. Свойства отображаются в **свойства** окно при выборе узла.  
  
 Существует два типа пользовательских свойств, которые можно добавить к узлу.  
  
-   Свойства, отображающие набор только для чтения данных с сайта SharePoint. Данные описывает компонент SharePoint, которую представляет узел. Пошаговое руководство, демонстрирующее, как это сделать, см. [Пошаговое руководство: расширение обозревателя серверов для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Свойства, отображающие пользовательские чтения и записи данных. Пример кода, в котором показано, как это сделать, см. [как: расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="getting-data-for-built-in-nodes"></a>Получение данных для встроенных узлов  
 Все встроенные узлы, предоставляемые Visual Studio содержат определенные данные о компоненте SharePoint, который они представляют. Например узел, представляющий список на сайте SharePoint предоставляет некоторые данные об этом списке, такие как название и URL-адрес представления по умолчанию для списка.  
  
 Доступ к этим данным, получить объект данных от <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> , представляющий узел, которые вас интересуют. Тип объекта данных зависит от типа узла.  
  
 В следующем примере кода показано, как получить объект данных для узла списка. Этот пример в контексте полного примера см. в разделе [как: получение данных для встроенного узла SharePoint в обозревателе серверов](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]  
  
 Ниже перечислены типы объектов данных для каждого типа встроенного узла.  
  
|Тип узла|Тип объекта данных|  
|---------------|----------------------|  
|Узел веб-узла SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Тип содержимого|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Функция|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Поле|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|Список|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Шаблон списка|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Представление списка (Microsoft.SharePoint.SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Сопоставление рабочего процесса|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Шаблон рабочего процесса|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство, в разделе [связывание пользовательских данных с расширениями средств SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Расширение обозревателя серверов для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Как: расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Способ: добавить пользовательского узла SharePoint в обозревателе серверов](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Как: получение данных для встроенного узла SharePoint в обозревателе серверов](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Связывание пользовательских данных с расширениями средств SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Просмотр подключений SharePoint с помощью обозревателя серверов](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Расширение инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  