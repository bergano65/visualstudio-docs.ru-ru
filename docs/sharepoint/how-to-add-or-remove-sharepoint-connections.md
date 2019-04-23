---
title: Практическое руководство. Добавление и удаление подключений SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 70594f8c881289bd394f33353f237bdab71c91f1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077372"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>Практическое руководство. Добавление и удаление подключений SharePoint
  Обозреватель серверов позволяет просматривать сайты SharePoint, а также для подключения к данным. Тем не менее, чтобы можно было просматривать содержимое на сайте SharePoint необходимо добавить его в **подключения SharePoint** узла.

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>Чтобы добавить сайт SharePoint для узла подключений SharePoint

1. В строке меню выберите **представление**, **обозревателя серверов**.

2. В **обозревателя серверов**, выберите **подключения SharePoint** узел, а затем в строке меню выберите **средства** > **добавить SharePoint Подключение**.

3. В **Добавление подключения SharePoint** введите [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] для сайта SharePoint (например, http://testserver/sites/unittests).

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>Для удаления сайта SharePoint из узла подключений SharePoint

1. В строке меню выберите **представление**, **обозревателя серверов** открыть **обозревателя серверов**.

2. Разверните **подключения SharePoint** узел, чтобы открыть сайт SharePoint, который требуется удалить из **обозревателя серверов**.

3. Выберите сайт, а затем в строке меню выберите **изменить** > **удалить**.

    > [!NOTE]
    >  Этот шаг не удаляет сам сайт; он удаляется только подключение из **обозревателя серверов**.

## <a name="see-also"></a>См. также
- [Просмотр подключений SharePoint с помощью обозревателя серверов](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
