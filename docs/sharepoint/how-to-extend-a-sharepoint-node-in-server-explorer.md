---
title: "Как: расширение узла SharePoint в обозревателе серверов | Документы Microsoft"
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
ms.assetid: 5e443950-12e6-40d1-864b-c384b6be4ce4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98dd11e74053bde9ad1ec2e23f4f663dfa7d1e1d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Практическое руководство. Расширение узла SharePoint в обозревателе сервера
  Можно расширить узлы, расположенные под **подключения SharePoint** узел в **обозревателя серверов**. Это полезно в том случае, если вы хотите добавить в существующий узел новые дочерние узлы, элементы контекстного меню или свойства. Дополнительные сведения см. в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Расширение узла SharePoint в обозревателе серверов  
  
1.  Создайте проект библиотеки классов.  
  
2.  Добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  
  
4.  Добавить <xref:System.ComponentModel.Composition.ExportAttribute> к классу атрибут. Этот атрибут позволяет Visual Studio находить и загружать вашей <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> реализации. Передайте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> тип в конструктор атрибута.  
  
5.  Добавить <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> к классу атрибут. Этот атрибут задает идентификатор строки для типа узла, который требуется расширить.  
  
     Чтобы указать узел встроенных типов, предоставляемых средой Visual Studio, передайте один из следующих значений перечисления конструктору атрибута:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Используется, эти значения, чтобы задать узлы подключения сайтов (узлы, отображающие URL-адреса сайта), узлы сайтов и все другие родительские узлы в **обозревателя серверов**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Используется эти значения для указания одного из встроенных узлов, представляющих отдельный компонент на сайте SharePoint, например узел, представляющий список, поле или тип содержимого.  
  
6.  В реализации <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> метод помощью членов *nodeType* параметр для добавления элементов на узле. Этот параметр является <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> объект, предоставляющий доступ к событиям, определенным в <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> интерфейса. Например можно обрабатывать следующие события:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Обрабатываете, чтобы добавить новые дочерние узлы узла. Дополнительные сведения см. в разделе [как: добавить пользовательского узла SharePoint в обозревателе серверов](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Обрабатываете это событие для добавления пользовательского контекстного меню к узлу.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Это событие обрабатывается для добавления пользовательских свойств на узел. Свойства отображаются в **свойства** окно при выборе узла.  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется создание двух различных типов расширений узла:  
  
-   Расширение, которое добавляет пункт контекстного меню для узлов сайта SharePoint. Пункт меню отображается имя узла, который был щелкнут.  
  
-   Расширение, которое добавляет пользовательское свойство с именем **ContosoExampleProperty** на каждый узел, представляющий поле с именем **текст**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
 Это расширение добавляет свойство редактируемой строки к узлам. Можно также создать пользовательские свойства для отображения только для чтения данных с сервера SharePoint. Пример, демонстрирующий, как это сделать см. в разделе [Пошаговое руководство: расширение обозревателя серверов для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms.  
  
## <a name="deploying-the-extension"></a>Развертывание расширения  
 Для развертывания **обозревателя серверов** расширения, создать [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Способ: добавить пользовательского узла SharePoint в обозревателе серверов](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Пошаговое руководство: Расширение обозревателя серверов для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Связь пользовательских данных с расширениями средств SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  