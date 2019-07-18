---
title: Практическое руководство. Добавление в обозреватель сервера пользовательского узла SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8ece5c207a0244a55078ef44f9156e7e95cedf5c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62556693"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Практическое руководство. Добавить пользовательский узел SharePoint в обозревателе серверов
  Можно добавить пользовательские узлы под **подключения SharePoint** узел в **обозревателя серверов**. Это полезно, если требуется отображать дополнительные компоненты SharePoint, которые не отображаются в **обозревателя серверов** по умолчанию. Дополнительные сведения см. в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

 Чтобы добавить пользовательский узел, сначала создайте класс, определяющий новый узел. Создайте расширение, которое добавляет узел в качестве дочернего элемента существующим узлом.

### <a name="to-define-the-new-node"></a>Для определения нового узла

1. Создайте проект библиотеки классов.

2. Добавьте ссылки на следующие сборки:

    - Microsoft.VisualStudio.SharePoint

    - Microsoft.VisualStudio.SharePoint.Explorer.Extensions

    - System.ComponentModel.Composition

    - System.Drawing;

3. Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.

4. Добавьте следующие атрибуты к классу:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Этот атрибут позволяет Visual Studio для обнаружения и загрузки вашего <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> реализации. Передайте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> тип конструктору атрибута.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. В определении узла этот атрибут задает идентификатор строки для нового узла. Мы рекомендуем использовать формат *название компании*. *Имя узла* чтобы убедиться в том, что все узлы имеют уникальный идентификатор.

5. В реализации <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> метода, используйте членами *typeDefinition* параметра для настройки поведения нового узла. Этот параметр является <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> объект, предоставляющий доступ к событиям, определенным в <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> интерфейс.

     В следующем примере кода показано, как определить новый узел. В этом примере предполагается, что проект содержит значок с именем CustomChildNodeIcon как внедренный ресурс.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]

### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Чтобы добавить новый узел в качестве дочернего элемента существующий узел

1. В проекте, определении узла, создайте класс, реализующий <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> интерфейс.

2. Добавьте к классу атрибут <xref:System.ComponentModel.Composition.ExportAttribute> . Этот атрибут позволяет Visual Studio для обнаружения и загрузки вашего <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> реализации. Передайте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> тип конструктору атрибута.

3. Добавьте к классу атрибут <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> . В расширении узла этот атрибут задает идентификатор строки для типа узла, который требуется расширить.

     Чтобы указать узел встроенных типов, предоставляемых средой Visual Studio, передайте один из следующих значений перечисления конструктору атрибута:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Используйте эти значения для указания узлов подключения к сайту (узлы, отображающие URL-адреса сайта), узлы сайтов и все остальные родительские узлы в **обозревателя серверов**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Эти значения можно используйте для указания одного из встроенных узлов, представляющих отдельный компонент на сайте SharePoint, например узел, представляющий список, поле или тип содержимого.

4. В реализации <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> метод, дескриптор <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> событие <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> параметра.

5. В <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> обработчик событий, добавить новый узел в коллекцию дочерних узлов объекта <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> объекта, предоставленного параметра аргументов события.

     В следующем примере кода демонстрируется добавление нового узла в качестве дочернего элемента узла сайта SharePoint в **обозревателя серверов**.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]

## <a name="complete-example"></a>Полный пример
 В следующем примере кода представлен полный код для определения простого узла и добавить его в качестве дочернего элемента узла сайта SharePoint в **обозревателя серверов**.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]

## <a name="compiling-the-code"></a>Компиляция кода
 В этом примере предполагается, что проект содержит значок с именем CustomChildNodeIcon как внедренный ресурс. В этом примере также требуются ссылки на следующие сборки:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

- System.Drawing;

## <a name="deploy-the-extension"></a>Развертывание расширения
 Для развертывания **обозревателя серверов** расширение, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывания расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также
- [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Практическое руководство. Расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Пошаговое руководство: Расширения обозревателя сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
