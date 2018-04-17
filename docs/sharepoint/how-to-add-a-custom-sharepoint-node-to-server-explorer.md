---
title: 'Способ: добавить пользовательского узла SharePoint в обозревателе серверов | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47b51070a3f3368dbff636858c9a2e1ebf2e9f80
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Практическое руководство. Добавление в обозреватель сервера пользовательского узла SharePoint
  Можно добавлять пользовательские узлы под **подключения SharePoint** узел в **обозревателя серверов**. Это полезно, если требуется отображать дополнительные компоненты SharePoint, которые не отображаются в **обозревателя серверов** по умолчанию. Дополнительные сведения см. в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
 Чтобы добавить пользовательский узел, сначала создайте класс, определяющий новый узел. Затем создайте расширение, которое добавляет узел в качестве дочернего для имеющегося узла.  
  
### <a name="to-define-the-new-node"></a>Для определения нового узла  
  
1.  Создайте проект библиотеки классов.  
  
2.  Добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing;  
  
3.  Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  
  
4.  Добавьте в класс следующие атрибуты:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Этот атрибут позволяет Visual Studio находить и загружать вашей <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> реализации. Передайте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> тип в конструктор атрибута.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. В определении узла этот атрибут задает идентификатор строки для нового узла. Мы рекомендуем использовать формат *название компании*. *Имя узла* чтобы убедиться в том, что все узлы иметь уникальный идентификатор.  
  
5.  В реализации <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> метод помощью членов *typeDefinition* параметр, можно настроить поведение нового узла. Этот параметр является <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> объект, предоставляющий доступ к событиям, определенным в <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> интерфейса.  
  
     В следующем примере кода демонстрируется определение нового узла. В этом примере предполагается, что проект содержит значок с именем CustomChildNodeIcon как внедренный ресурс.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]  
  
### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Для добавления нового узла в качестве дочернего для имеющегося узла  
  
1.  В том же проекте, содержащем определение нового узла, создайте класс, реализующий <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> интерфейса.  
  
2.  Добавить <xref:System.ComponentModel.Composition.ExportAttribute> к классу атрибут. Этот атрибут позволяет Visual Studio находить и загружать вашей <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> реализации. Передайте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> тип в конструктор атрибута.  
  
3.  Добавить <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> к классу атрибут. В расширении узла этот атрибут задает идентификатор строки для типа узла, который требуется расширить.  
  
     Чтобы указать узел встроенных типов, предоставляемых средой Visual Studio, передайте один из следующих значений перечисления конструктору атрибута:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Используется, эти значения, чтобы задать узлы подключения сайтов (узлы, отображающие URL-адреса сайта), узлы сайтов и все другие родительские узлы в **обозревателя серверов**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Используется эти значения для указания одного из встроенных узлов, представляющих отдельный компонент на сайте SharePoint, например узел, представляющий список, поле или тип содержимого.  
  
4.  В реализации <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> метод, дескриптор <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> событие <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> параметра.  
  
5.  В <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> обработчика событий, добавить новый узел в коллекцию дочерних узлов объекта <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> объекта, предоставленного параметра аргументов события.  
  
     В следующем примере кода демонстрируется добавление нового узла в качестве дочернего узла сайта SharePoint в **обозревателя серверов**.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]  
  
## <a name="complete-example"></a>Полный пример  
 В следующем примере кода представлен полный код для определения простого узла и добавления его в качестве дочернего узла сайта SharePoint в **обозревателя серверов**.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 В этом примере предполагается, что проект содержит значок с именем CustomChildNodeIcon как внедренный ресурс. Кроме того, для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing;  
  
## <a name="deploying-the-extension"></a>Развертывание расширения  
 Для развертывания **обозревателя серверов** расширения, создать [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Как: расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Пошаговое руководство. Расширение обозревателя сервера, так чтобы в нем отображались веб-части](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  