---
title: Работа с концептуальной моделью(службы данных WCF)
description: Работа с концептуальной моделью в службы данных WCF. Запрашивать данные через объекты вместо перевода между схемами базы данных и объектными моделями.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], querying a service
- data [Visual Studio], LINQ to Entities
- data [Visual Studio], querying an EDM
ms.assetid: 2cd873cf-b010-49f2-a278-bb1277aaa934
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ef5745f974848da75b4dcc0c42b59b38aa61cd0b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866116"
---
# <a name="work-with-a-conceptual-model-wcf-data-services"></a>Работа с концептуальной моделью (службы данных WCF)

При использовании концептуальной модели для описания данных в базе данных можно запрашивать данные через объекты, а не перемещаться между схемой базы данных и объектной моделью.

Концептуальные модели можно использовать с службы данных WCFными приложениями. В следующих разделах показано, как запрашивать данные с помощью концептуальной модели.

| Раздел | Описание |
| - | - |
| [Инструкции. выполнение запросов службы данных](/dotnet/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services) | Показывает, как запросить службу данных из приложения .NET. |
| [Как выполнить запрос проекта к результатам запроса](/dotnet/framework/data/wcf/how-to-project-query-results-wcf-data-services) | Показывает, как уменьшить объем данных, возвращаемых с помощью запроса службы данных. |

При использовании концептуальной модели можно определить допустимый тип данных на языке, соответствующем вашему домену. В модели можно определить допустимые данные или добавить проверку в операции, выполняемые с сущностью или службой данных.

В следующих разделах показано, как добавить проверку в службы данных WCF приложения.

|Раздел|Описание|
|-----------|-----------------|
|[Как перехватывать сообщения службы данных](/dotnet/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services)|Показывает, как добавить проверку в операцию службы данных.|

 В следующих разделах показано, как создавать, обновлять и удалять данные, выполняя операции с сущностями.

|Раздел|Описание|
|-----------|-----------------|
|[Как добавлять, изменять и удалять сущности](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)|Показывает, как создавать, обновлять и удалять данные сущностей в службе данных.|
|[Руководство. Определение связей сущностей](/dotnet/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services)|Показывает, как создавать или изменять связи в службе данных.|

## <a name="see-also"></a>См. также раздел

- [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Выполнение запросов к службе данных](/dotnet/framework/data/wcf/querying-the-data-service-wcf-data-services)
