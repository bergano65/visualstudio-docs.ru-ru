---
title: Обращение к модели объекта SharePoint | Документация Майкрософт
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24634143a40f7b163c0b658bddb5596041868033
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62988400"
---
# <a name="call-into-the-sharepoint-object-models"></a>Вызов объектных моделей SharePoint
  При создании расширений для инструментов SharePoint в Visual Studio, возможно, для вызова API-интерфейсы SharePoint для выполнения определенных задач. Например при создании пользовательского шага развертывания для проектов SharePoint, может потребоваться вызвать API-интерфейсы для выполнения некоторых задач для развертывания решений SharePoint.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] и [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] предоставляют две разные объектные модели, которые можно использовать в расширениях инструментов SharePoint: Серверная объектная модель и объектную модель клиента. Каждая объектная модель имеет преимущества и недостатки в контексте расширений инструментов SharePoint.

 Обзор объектной модели SharePoint, см. в разделе [Обзор модели программирования SharePoint расширений средств](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="use-the-client-object-model-in-extension-projects"></a>Использование клиентской объектной модели в проектах расширений
 При разработке расширения инструментов SharePoint, можно использовать клиентскую объектную модель в проекте, как и любым другим набором управляемых интерфейсов API. Можно добавить ссылки на сборки в клиентской объектной модели в проект и интерфейсы API в клиентской объектной модели можно вызвать непосредственно из программного кода.

 Тем не менее клиентская объектная модель имеет два недостатка в контексте расширений инструментов SharePoint:

- Клиентская объектная модель предоставляет только подмножество серверной объектной модели. Если вам нужно использовать функции SharePoint, которые не представлены в объектной модели клиента, необходимо использовать серверную объектную модель.

- Несмотря на то, что с помощью клиентской объектной модели в расширениях инструментов SharePoint должна работать в большинстве случаев, могут возникнуть некоторые сценарии, где вызовы в объектную модель клиента не работают должным образом. Клиентская объектная модель предназначена для использования в клиентских приложениях для вызова сайтов SharePoint на удаленном сервере или ферме SharePoint. Средства SharePoint в Visual Studio работает только с локальной установки SharePoint на компьютере разработчика. Таким образом при использовании клиентской объектной модели в расширения инструментов SharePoint вызове с сайтом SharePoint на локальном компьютере, который является не то, как клиентская объектная модель была разработана для использования.

  Пошаговое руководство, которое демонстрирует использование клиентской объектной модели в расширении инструментов SharePoint в Visual Studio, см. в разделе [Пошаговое руководство: Вызов клиентской объектной модели SharePoint в расширении обозревателя серверов](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="use-the-server-object-model-in-extension-projects"></a>Используйте серверную объектную модель в проектах расширений
 Серверную объектную модель является надмножеством клиентской объектной модели. При использовании объектной модели сервера, можно использовать все возможности, [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] и [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] программным образом.

 Расширения инструментов SharePoint можно использовать интерфейсы API в серверную объектную модель, но они не могут напрямую вызывать API-интерфейсы. Серверную объектную модель может вызываться только из 64-разрядном процессе, ориентированном на .NET Framework 3.5. Тем не менее, расширения инструментов SharePoint требуют [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и выполняются в 32-разрядном процессе Visual Studio. Это предотвращает ссылок на сборки серверной объектной модели SharePoint непосредственно расширения инструментов SharePoint.

 Если вы хотите использовать серверную объектную модель в расширения инструментов SharePoint, необходимо создать пользовательский *команды SharePoint* для вызова API. Команда SharePoint определяется в дополнительной сборке, которая может напрямую вызывать серверную объектную модель. В проекте расширения вызывается команда SharePoint косвенно с помощью метода ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объекта.

 Дополнительные сведения о создании и использовании команд SharePoint см. в разделе [как: Создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) и [как: Выполнение команды SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Сведения о развертывании команд SharePoint, см. в разделе [развертывания расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Пошаговые руководства, которые демонстрируют, как создать и использовать команды SharePoint, см. в разделе [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) и [Пошаговое руководство: Расширения обозревателя сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

### <a name="understand-how-sharepoint-commands-are-executed"></a>Понять, как выполняются команды SharePoint
 Сборки, которые определяют команды SharePoint были загружены в 64-разрядных хост-процесс с именем *vssphost4.exe*. После вызова команды SharePoint в расширения инструментов SharePoint, команда будет выполнена по *vssphost4.exe* вместо 32-разрядном процессе Visual Studio (*devenv.exe*). Можно управлять некоторыми аспектами выполнения команды SharePoint, установив значения в реестре. Дополнительные сведения см. в разделе [отладка расширений для инструментов SharePoint в Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также
- [Практическое руководство. Создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Практическое руководство. Выполнение команды SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Обзор модели программирования SharePoint средств расширения](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
