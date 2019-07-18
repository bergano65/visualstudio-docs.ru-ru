---
title: Практическое руководство. Расширение узла SharePoint в обозревателе серверов | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c5e617b57437033f4194d96647ebff9d1c4e2c2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62814001"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Практическое руководство. Расширение узла SharePoint в обозревателе серверов
  Вы можете расширить узлы под **подключения SharePoint** узел в **обозревателя серверов**. Это полезно в том случае, если вы хотите добавить в существующий узел новые дочерние узлы, элементы контекстного меню или свойства. Дополнительные сведения см. в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Для расширения узла SharePoint в обозревателе серверов

1. Создайте проект библиотеки классов.

2. Добавьте ссылки на следующие сборки:

    - Microsoft.VisualStudio.SharePoint

    - Microsoft.VisualStudio.SharePoint.Explorer.Extensions

    - System.ComponentModel.Composition

3. Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.

4. Добавьте к классу атрибут <xref:System.ComponentModel.Composition.ExportAttribute> . Этот атрибут позволяет Visual Studio для обнаружения и загрузки вашего <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> реализации. Передайте <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> тип конструктору атрибута.

5. Добавьте к классу атрибут <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> . Этот атрибут задает идентификатор строки для типа узла, который требуется расширить.

     Чтобы указать узел встроенных типов, предоставляемых средой Visual Studio, передайте один из следующих значений перечисления конструктору атрибута:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Используйте эти значения для указания узлов подключения к сайту (узлы, отображающие URL-адреса сайта), узлы сайтов и все остальные родительские узлы в **обозревателя серверов**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Эти значения можно используйте для указания одного из встроенных узлов, представляющих отдельный компонент на сайте SharePoint, например узел, представляющий список, поле или тип содержимого.

6. В реализации <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> метода, используйте членами *nodeType* параметр для добавления функций к узлу. Этот параметр является <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> объект, предоставляющий доступ к событиям, определенным в <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> интерфейс. Например можно обрабатывать следующие события:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Обработайте это событие, чтобы добавить новые дочерние узлы к узлу. Дополнительные сведения см. в разделе [Как Добавить пользовательский узел SharePoint в обозревателе серверов](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Обработайте это событие, чтобы добавить элемент пользовательского контекстного меню к узлу.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Обработайте это событие, чтобы добавить пользовательские свойства к узлу. Свойства отображаются в **свойства** окно при выборе узла.

## <a name="example"></a>Пример
 В следующем примере кода демонстрируется создание двух различных типов расширений узла:

- Расширение, пункт контекстного меню для узлов сайта SharePoint. Если щелкнуть элемент меню, его имя узла, который был щелкнут.

- Расширение, которое добавляет пользовательское свойство с именем **ContosoExampleProperty** на каждый узел, представляющий поле с именем **текст**.

  [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
  [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]

  Это расширение добавляет свойство редактируемой строки к узлам. Можно также создать пользовательские свойства, которые отображают только для чтения данных с сервера SharePoint. Пример, в котором показано, как это сделать, см. в разделе [Пошаговое руководство: Расширения обозревателя сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="compile-the-code"></a>Компиляция кода
 В этом примере требуются ссылки на следующие сборки:

- Microsoft.VisualStudio.SharePoint

- Microsoft.VisualStudio.SharePoint.Explorer.Extensions

- System.ComponentModel.Composition

- System.Windows.Forms.

## <a name="deploy-the-extension"></a>Развертывание расширения
 Для развертывания **обозревателя серверов** расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывания расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также
- [Практическое руководство. Добавить пользовательский узел SharePoint в обозревателе серверов](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Пошаговое руководство: Расширения обозревателя сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Связывать пользовательские данные с расширениями средств SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
