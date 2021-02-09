---
title: Вызов объектных моделей SharePoint | Документация Майкрософт
description: Узнайте, как вызывать две различные объектные модели, которые можно использовать в расширениях инструментов SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 14358b5cc84f63227fd5001731c261002a324492
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928943"
---
# <a name="call-into-the-sharepoint-object-models"></a>Вызов объектных моделей SharePoint
  При создании расширений для инструментов SharePoint в Visual Studio может потребоваться вызывать API SharePoint для выполнения определенных задач. Например, если создать настраиваемый шаг развертывания для проектов SharePoint, то, возможно, придется вызывать API SharePoint для выполнения некоторых задач по развертыванию решений.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] и [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] предоставляют две различные объектные модели, которые можно использовать в расширениях инструментов SharePoint: серверной объектной модели и клиентской объектной модели. У каждой модели объектов есть преимущества и недостатки в контексте расширений инструментов SharePoint.

 Общие сведения об объектных моделях SharePoint см. [в разделе Общие сведения о модели программирования расширений инструментов SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="use-the-client-object-model-in-extension-projects"></a>Использование клиентской объектной модели в проектах расширений
 При разработке расширения для инструментов SharePoint можно использовать объектную модель клиента в проекте, как и любой другой набор управляемых API. В проект можно добавить ссылки на сборки в клиентской объектной модели, а также вызывать API в клиентской модели объектов непосредственно из кода.

 Однако в контексте расширений инструментов SharePoint у клиентской объектной модели есть два недостатка:

- Клиентская объектная модель предоставляет только подмножество серверной объектной модели. Если необходимо использовать функции SharePoint, не предоставляемые клиентской объектной моделью, необходимо использовать объектную модель сервера.

- Несмотря на то, что использование клиентской объектной модели в расширениях инструментов SharePoint должно работать в большинстве случаев, могут возникнуть ситуации, когда вызовы к клиентской объектной модели не работают должным образом. Клиентская объектная модель предназначена для использования в клиентских приложениях для вызова сайтов SharePoint на удаленном сервере или ферме. Средства SharePoint в Visual Studio работают только с локальной установкой SharePoint на компьютере разработчика. Таким образом, при использовании клиентской объектной модели в расширении инструментов SharePoint вы вызываете сайт SharePoint на локальном компьютере, который не предназначен для использования объектной модели клиента.

  Пошаговое руководство по использованию клиентской объектной модели в расширении инструментов SharePoint в Visual Studio см. в разделе [Пошаговое руководство. вызов клиентской объектной модели SharePoint в расширении обозреватель сервера](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="use-the-server-object-model-in-extension-projects"></a>Использование серверной объектной модели в проектах расширений
 Объектная модель сервера является надмножеством клиентской объектной модели. При использовании серверной объектной модели можно использовать все функции, [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] предоставляемые программно.

 Расширения инструментов SharePoint могут использовать интерфейсы API в серверной модели объектов, но они не могут вызывать API напрямую. Объектную модель сервера можно вызывать только из 64-разрядного процесса, предназначенного для платформа .NET Framework 3,5. Однако для расширений инструментов SharePoint требуются [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и, и они выполняются в 32-разрядном процессе Visual Studio. Это предотвращает прямую ссылку на сборки в объектной модели сервера SharePoint с помощью расширений инструментов SharePoint.

 Если вы хотите использовать объектную модель сервера в расширении инструментов SharePoint, необходимо создать пользовательскую *команду SharePoint* для вызова API. Команда SharePoint определяется во вторичной сборке, которая может напрямую вызывать серверную объектную модель. В проекте расширения команда SharePoint вызывается опосредованно с помощью метода ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объекта.

 Дополнительные сведения о создании и использовании команд SharePoint см. [в разделе инструкции. Создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) и [инструкции: выполнение команды SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Дополнительные сведения о развертывании команд SharePoint см. [в разделе Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Пошаговые руководства, демонстрирующие создание и использование команд SharePoint, см. в разделе Пошаговое [руководство. Создание настраиваемого шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) и [Пошаговое руководство. расширение обозреватель сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

### <a name="understand-how-sharepoint-commands-are-executed"></a>Сведения о выполнении команд SharePoint
 Сборки, определяющие команды SharePoint, загружаются в 64-разрядном размещающем процессе с именем *vssphost4.exe*. После вызова команды SharePoint в расширении инструментов SharePoint команда выполняется *vssphost4.exe* вместо 32-разрядного процесса Visual Studio (*devenv.exe*). Вы можете управлять некоторыми аспектами выполнения команд SharePoint, задавая значения в реестре. Дополнительные сведения см. в разделе [расширения отладки для инструментов SharePoint в Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Как создать команду SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Инструкции: выполнение команды SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Обзор модели программирования расширений инструментов SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
