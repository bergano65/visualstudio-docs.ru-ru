---
title: Получение данных для встроенного узла SharePoint в обозреватель сервера
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 7649092cc21fcc7b861f4ddf630007bde896e852
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585775"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Пошаговое руководство. получение данных для встроенного узла SharePoint в обозреватель сервера
  Для каждого встроенного узла SharePoint в **Обозреватель сервера**можно получить данные для базового компонента SharePoint, представляемого узлом. Дополнительные сведения см. в разделе [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="example"></a>Пример
 В следующем примере кода показано, как получить данные для базового списка SharePoint, представленного узлом списка в **Обозреватель сервера**. По умолчанию список узлов имеет **вид в** элементе контекстного меню браузера, который можно щелкнуть, чтобы открыть списки в веб-браузере. Этот пример расширяет список узлов, добавляя **представление в** элемент контекстного меню Visual Studio, которое открывает списки непосредственно в Visual Studio. Код получает доступ к данным списка для узла, чтобы получить URL-адрес списка, открываемого в Visual Studio.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]

 В этом примере используется служба проекта SharePoint для получения <xref:EnvDTE.DTE> объекта, который используется для открытия списков в Visual Studio. Дополнительные сведения о службе проектов SharePoint см. в статье [Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 Дополнительные сведения о базовых задачах по созданию расширения для узла SharePoint см. в разделе [как расширить узел SharePoint в обозреватель сервера](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются ссылки на следующие сборки:

- EnvDTE

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение **Обозреватель сервера** , создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и всех остальных файлов, которые требуется распространить с расширением. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также
- [Расширение узла подключений SharePoint в обозревателе сервера](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Руководство. расширение узла SharePoint в обозреватель сервера](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
