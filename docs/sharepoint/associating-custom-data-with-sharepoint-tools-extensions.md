---
title: Связь пользовательских данных с SharePoint расширений средств | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2f22647d646797426a6a49ff24257846e180b1d4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614081"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Связывать пользовательские данные с расширениями средств SharePoint
  Можно добавить пользовательские данные для определенных объектов в расширениях инструментов SharePoint. Это полезно при наличии данных в одной части вашего расширения, вам требуется доступ к более поздней версии из другого кода в модуле. Вместо реализации пользовательских способ хранения и доступа к данным, вы можете связать данные с объектом расширения и затем впоследствии извлекать данные из того же объекта.

 Добавление пользовательских данных в объекты удобно, если вы хотите сохранить данные, относящиеся к конкретному элементу в Visual Studio. Расширения инструментов SharePoint загружаются только в том случае, когда в Visual Studio, поэтому расширение может работать с несколькими различными элементами (таких как проекты, элементы, проекта или **обозревателя серверов** узлов) в любое время. При наличии пользовательских данных, которые относятся только к конкретному элементу, можно добавить данные в объект, представляющий элемент.

 При добавлении пользовательских данных к объектам в расширениях инструментов SharePoint, данные не сохраняются. Данные будут доступны только в течение времени существования объекта. После объект удаляется сборщиком мусора, данные будут потеряны.

 В расширениях системы проектов SharePoint можно также сохранить строковые данные, которые будет повторяться после выгрузки расширения. Дополнительные сведения см. в разделе [сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="objects-that-can-contain-custom-data"></a>Объекты, которые могут содержать пользовательские данные
 Можно добавить пользовательские данные к любому объекту в объектной модели инструментов SharePoint, реализующий <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> интерфейс. Этот интерфейс определяет только одно свойство <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, который является коллекцией пользовательских объектов данных. Следующие типы реализуют <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:

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

## <a name="add-and-retrieve-custom-data"></a>Добавление и извлечение пользовательских данных
 Чтобы добавить пользовательские данные в объект из расширения инструментов SharePoint, получить <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойства объекта, который требуется добавить данные, а затем используйте <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> метод для добавления данных к объекту.

 Чтобы получить пользовательские данные из объекта в расширения инструментов SharePoint, получить <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойства от объекта, а затем выполните одну из следующих методов:

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Этот метод возвращает **true** Если объект данных существует, или **false** если он не существует. Этот метод можно использовать для извлечения экземпляров типов значений и ссылочных типов.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Этот метод возвращает данные объекта, если он существует, или **null** если он не существует. Этот метод можно использовать только для извлечения экземпляров ссылочных типов.

  В следующем примере кода определяет, является ли определенный объект данных уже связан с элементом проекта. Если объект данных еще не связан с элементом проекта, а затем код добавляет объект в <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> свойства элемента проекта. Этот пример в контексте полного примера см. в разделе [как: Добавление свойства в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
  [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]

## <a name="see-also"></a>См. также
- [Основные понятия программирования и функции для расширения инструментов SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Пошаговое руководство: Расширение обозревателя сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Практическое руководство. Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Практическое руководство. Добавление свойства в пользовательский тип элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
