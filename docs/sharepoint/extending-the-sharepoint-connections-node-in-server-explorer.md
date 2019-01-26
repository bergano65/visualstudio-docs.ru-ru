---
title: Расширение узла подключений SharePoint в обозревателе серверов | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c10906f21a6379d0f1797fa7986e33a401de32f5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876139"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Расширение узла подключений SharePoint в обозревателе серверов
  В Visual Studio, вы можете подключиться к локальным сайтам SharePoint на компьютере разработчика с помощью **подключения SharePoint** узел в **обозревателя серверов** окна. Этот узел содержит многие компоненты локальных сайтов SharePoint в виде иерархического дерева. Например можно просмотреть списки, библиотеки документов и типов содержимого на локальных сайтах. Дополнительные сведения об использовании **обозревателя серверов** для подключения к локальным сайтам SharePoint, см. в разделе [подключений Обзор SharePoint с помощью обозревателя серверов](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 Вы можете расширить **подключения SharePoint** узла путем создания расширений для существующих узлов или путем создания пользовательский тип узла и добавления его в иерархию узлов.  
  
## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Задачи для расширение узла подключений SharePoint
 Чтобы расширить существующий узел, создать расширение Visual Studio, который реализует <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> интерфейс. При расширении узла, можно добавить функциональные возможности на узел, например собственные элементы контекстного меню или пользовательские свойства. Дополнительные сведения см. в разделе [Как Расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Чтобы создать пользовательский тип узла, создать расширение Visual Studio, который реализует <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> интерфейс. Создайте пользовательский узел, если вы хотите отображать компоненты сайтов SharePoint, которые не отображаются в **обозревателя серверов** по умолчанию. Например **обозревателя серверов** отображаются коллекции веб-части сайта SharePoint по умолчанию, но вы можете добавить пользовательский узел, который делает это. Дополнительные сведения см. в разделе [Как Добавить пользовательский узел SharePoint в обозревателе серверов](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) и [Пошаговое руководство: Расширения обозревателя сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="add-custom-properties-to-nodes"></a>Добавление пользовательских свойств в узлы
 При расширении узла или создать пользовательский тип узла, можно добавить пользовательские свойства к узлу. Свойства отображаются в **свойства** окно при выборе узла.  
  
 Существует два типа пользовательских свойств, которые можно добавить к узлу:  
  
-   Свойства, которые отображают набор только для чтения данных с сайта SharePoint. Данные описывается компонент SharePoint, которую представляет узел. Пошаговое руководство, которое демонстрирует, как это сделать, см. в разделе [Пошаговое руководство: Расширения обозревателя сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Свойства, которые отображают пользовательский чтения и записи данных. Пример кода, в котором показано, как это сделать, см. в разделе [как: Расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="get-data-for-built-in-nodes"></a>Получение данных для встроенных узлов
 Все встроенные узлы, предоставляемые Visual Studio включают некоторые данные о компоненте SharePoint, который они представляют. Например узел, представляющий список на сайте SharePoint предоставляет некоторые данные о списке, такие как заголовок и URL-адрес представления по умолчанию для списка.  
  
 Доступ к этим данным, получить объект данных из <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> , представляющий узел, которые вас интересуют. Тип объекта данных зависит от типа узла.  
  
 В следующем примере кода показано, как получить объект данных для узла списка. Этот пример в контексте полного примера см. в разделе [как: Получение данных для встроенного узла SharePoint в обозревателе серверов](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]  
  
 Ниже перечислены типы объектов данных для каждого типа встроенного узла.  
  
|Тип узла|Тип объекта данных|  
|---------------|----------------------|  
|Узел сайта SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Тип содержимого|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Функция|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Поле|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|Список|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Шаблон списка|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Представление списка (Microsoft.SharePoint.SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Сопоставление рабочего процесса|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Шаблон рабочего процесса|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Дополнительные сведения об использовании <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойство, см. в разделе [расширений средств сопоставления пользовательских данных с SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="see-also"></a>См. также
 [Пошаговое руководство: Расширения обозревателя сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Практическое руководство. Расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Практическое руководство. Добавить пользовательский узел SharePoint в обозревателе серверов](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Практическое руководство. Получение данных для встроенного узла SharePoint в обозревателе серверов](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Связывать пользовательские данные с расширениями средств SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Просмотр подключений SharePoint с помощью обозревателя серверов](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Расширения инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
