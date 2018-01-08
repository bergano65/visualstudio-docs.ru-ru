---
title: "Обращение к объектной модели SharePoint | Документы Microsoft"
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
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
ms.assetid: 99934f9e-901e-464e-ac8c-22c6c86440f4
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b1a0f4175dc884283dcf92b7f6268a518cdaf0ca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="calling-into-the-sharepoint-object-models"></a>Вызов объектных моделей SharePoint
  При создании расширений для средств SharePoint в Visual Studio, может потребоваться вызов API SharePoint для выполнения определенных задач. Например при создании пользовательского шага развертывания для проектов SharePoint, может потребоваться вызвать API-интерфейсы SharePoint для выполнения некоторых задач для развертывания решений.  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]и [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] предоставляют две разные объектные модели, которые можно использовать в расширениях инструментов SharePoint: Серверная объектная модель и клиентской объектной модели. Каждая объектная модель имеет преимущества и недостатки в контексте расширений инструментов SharePoint.  
  
 Общие сведения об объектной модели SharePoint см. в разделе [Общие сведения о программировании модели из расширения инструментов SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="using-the-client-object-model-in-extension-projects"></a>С помощью клиентской объектной модели в проектах расширений  
 При разработке расширения для средств SharePoint клиентской объектной модели можно использовать в проекте, как и любым другим набором управляемых интерфейсов API. В проект можно добавлять ссылки на сборки в клиентской объектной модели и может вызывать API в клиентской объектной модели непосредственно из программного кода.  
  
 Однако клиентская объектная модель имеет два недостатка в контексте расширений инструментов SharePoint.  
  
-   Клиентская объектная модель предоставляет только подмножество серверной объектной модели. Если необходимо использовать функции SharePoint, которые не представлены в клиентской объектной модели, необходимо использовать объектную модель сервера.  
  
-   Несмотря на то, что клиентской объектной модели в расширениях инструментов SharePoint должна работать в большинстве случаев, возможны некоторые сценарии, где вызовы к клиентской объектной модели, не работают должным образом. Клиентская объектная модель предназначена для использования в клиентских приложениях для вызова сайтов SharePoint на удаленном сервере или ферме SharePoint. Средства SharePoint в Visual Studio работает только с локальной установки SharePoint на компьютере разработчика. Таким образом при использовании клиентской объектной модели в расширении инструментов SharePoint можно вызывать сайта SharePoint на локальном компьютере, который является не как клиентской объектной модели, которые были предназначены для использования.  
  
 Пошаговое руководство демонстрирует использование клиентской объектной модели в расширении инструментов SharePoint в Visual Studio см. в разделе [Пошаговое руководство: вызов клиентской объектной модели SharePoint в расширении обозревателя серверов](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="using-the-server-object-model-in-extension-projects"></a>Использование серверной объектной модели в проектах расширений  
 Серверная объектная модель является надмножеством клиентской объектной модели. При использовании серверной объектной модели можно использовать все возможности, [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] и [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] программным образом.  
  
 Расширения инструментов SharePoint можно использовать API в серверной объектной модели, но они не могут вызывать интерфейсы API напрямую. Серверная объектная модель может вызываться только из 64-разрядном процессе, ориентированном на .NET Framework 3.5. Однако для расширения инструментов SharePoint требуется [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и выполняются в 32-разрядном процессе Visual Studio. Это предотвращает ссылок на сборки серверной объектной модели SharePoint непосредственно расширения инструментов SharePoint.  
  
 Если вы хотите использовать в расширении инструментов SharePoint в серверную объектную модель, необходимо создать пользовательский *команда SharePoint* для вызова API. Команда SharePoint определяется в дополнительной сборке, которая может напрямую вызывать серверную объектную модель. В проекте расширения вызывается команда SharePoint косвенно с помощью метода ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> объекта.  
  
 Дополнительные сведения о создании и использовании команд SharePoint см. в разделе [как: создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) и [как: выполнение команды SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Сведения о развертывании команд SharePoint см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Примеры, демонстрирующие способы создания и использования команд SharePoint, см. [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) и [Пошаговое руководство: расширение обозревателя серверов в Интернете отображения Части](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### <a name="understanding-how-sharepoint-commands-are-executed"></a>Основные сведения о том, как выполнения команд SharePoint  
 В 64-разрядный процесс так называемого vssphost4.exe загружаются сборки, которые определяют команд SharePoint. После вызова команды SharePoint из расширения инструментов SharePoint, команда выполняется с vssphost4.exe вместо 32-разрядном процессе Visual Studio (devenv.exe). Можно управлять некоторыми аспектами выполнения команды SharePoint, задавая значения в реестре. Дополнительные сведения см. в разделе [отладка расширений для средств SharePoint в Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Как: создание команды SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Как: выполнение команды SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Обзор модели программирования для расширений средств SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  