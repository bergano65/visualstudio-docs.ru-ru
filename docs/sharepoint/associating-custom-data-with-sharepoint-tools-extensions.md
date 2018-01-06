---
title: "Связывание пользовательских данных с SharePoint расширений средств | Документы Microsoft"
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
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
ms.assetid: cfc87272-85a1-4c36-89e4-2662417d59ea
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 24525e553fabfd05972cbe2ee59fa1260d3b855b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="associating-custom-data-with-sharepoint-tools-extensions"></a>Связь пользовательских данных с расширениями средств SharePoint
  Можно добавить пользовательские данные в определенные объекты в расширениях инструментов SharePoint. Это полезно при наличии данных в одной части расширение, необходимо получить доступ к более поздней версии из другого кода в модуль. Вместо реализации пользовательского способа хранения и доступа к данным, можно связать данные с объектом в расширении и затем впоследствии извлекать данные из одного объекта.  
  
 Добавление пользовательских данных в объекты также полезен, если вы хотите сохранить данные, относящиеся к конкретному элементу в Visual Studio. Расширения инструментов SharePoint загружаются только в том случае, когда в Visual Studio, поэтому расширение может работать с несколькими различными элементами (таких как проекты, элементы, проекта или **обозревателя серверов** узлов) в любое время. Если у вас есть пользовательские данные, относящиеся только к конкретному элементу, можно добавить данные в объект, представляющий этот элемент.  
  
 При добавлении пользовательских данных в объекты в расширениях инструментов SharePoint, данные не сохраняются. Данные будут доступны только в течение времени существования объекта. После объект будет удален при сборке мусора, данные будут потеряны.  
  
 В расширениях системы проектов SharePoint можно также сохранить строковые данные, которые должны оставаться неизменными после выгрузки расширения. Дополнительные сведения см. в разделе [сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="objects-that-can-contain-custom-data"></a>Объекты, которые могут содержать пользовательские данные  
 Можно добавить пользовательские данные для любого объекта в объектной модели инструментов SharePoint, реализующий <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> интерфейса. Этот интерфейс определяет только одно свойство <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, которое является коллекцией объектов пользовательских данных. Следующие типы реализуют интерфейс <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## <a name="adding-and-retrieving-custom-data"></a>Добавление и извлечение пользовательских данных  
 Чтобы добавить пользовательские данные в объект в расширении инструментов SharePoint, получить <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойства объекта, который требуется добавить данные, а затем использовать <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> метод, чтобы добавить данные к объекту.  
  
 Чтобы получить пользовательские данные из объекта в расширении инструментов SharePoint, получить <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойства от объекта, а затем выполните одну из следующих методов:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Этот метод возвращает **true** , если объект данных существует, или **false** , если он не существует. Этот метод можно использовать для извлечения экземпляров типов значений и ссылочных типов.  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Этот метод возвращает данные объекта, если он существует, или **null** , если он не существует. Этот метод можно использовать только для извлечения экземпляров ссылочных типов.  
  
 В следующем примере кода определяет, является ли определенный объект данных уже связан с элементом проекта. Если объект данных не связан с элементом проекта, а затем код добавляет объект в <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойства элемента проекта. Этот пример в контексте полного примера см. в разделе [как: добавить свойство в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>См. также  
 [Основные понятия программирования и функции расширений SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Пошаговое руководство: Расширение обозревателя серверов для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Как: Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Как: добавить свойство типа элемента проекта SharePoint пользовательских] (.. /SharePoint/How-to-Add-a-Property-to-a-custom-SharePoint-Project-Item-Type.md   
  