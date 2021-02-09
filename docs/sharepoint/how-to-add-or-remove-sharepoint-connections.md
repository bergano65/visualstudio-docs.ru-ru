---
title: Как добавить или удалить подключения SharePoint | Документация Майкрософт
description: Добавление или удаление подключений SharePoint с помощью узла "подключения SharePoint" в окне обозреватель сервера Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 57ff132274ba7f720a845078b0424fe235d9c31e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923455"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>Практическое руководство. Добавление и удаление подключений SharePoint
  Обозреватель сервера позволяет просматривать сайты SharePoint и подключения к данным. Однако прежде чем можно будет просматривать содержимое сайта SharePoint, его необходимо добавить в узел **подключения SharePoint** .

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>Добавление сайта SharePoint в узел «подключения SharePoint»

1. В строке меню выберите **вид**, **Обозреватель сервера**.

2. В **Обозреватель сервера** выберите узел **подключения SharePoint** , а затем в строке меню выберите **Сервис**  >  **Добавить подключение SharePoint**.

3. В поле **Добавить подключение SharePoint** введите [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] для сайта SharePoint (например, http://testserver/sites/unittests) .

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>Удаление сайта SharePoint из узла "подключения SharePoint"

1. В строке меню выберите **вид**, **Обозреватель сервера** , чтобы открыть **Обозреватель сервера**.

2. Разверните узел **подключения SharePoint** , чтобы открыть сайт SharePoint, который требуется удалить из **Обозреватель сервера**.

3. Выберите сайт, а затем в строке меню выберите **изменить**  >  **Удалить**.

    > [!NOTE]
    > На этом этапе не удаляется базовый сайт. Он удаляет только подключение из **Обозреватель сервера**.

## <a name="see-also"></a>См. также раздел
- [Просмотр подключений SharePoint с помощью обозревателя сервера](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
