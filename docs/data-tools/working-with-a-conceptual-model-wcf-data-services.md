---
title: Работа с концептуальной моделью(службы данных WCF)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], querying a service
- data [Visual Studio], LINQ to Entities
- data [Visual Studio], querying an EDM
ms.assetid: 2cd873cf-b010-49f2-a278-bb1277aaa934
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7e92885e652c9456503bfa75fbce5640c377b684
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745339"
---
# <a name="work-with-a-conceptual-model-wcf-data-services"></a>Работа с концептуальной модели (службы данных WCF)

При использовании концептуальной модели для описания данных в базе данных, можно запросить данные через объекты вместо того, чтобы перевести вперед и назад между схему базы данных и модель объектов.

 Концептуальные модели можно использовать с приложениями WCF Data Services. Следующие разделы показывают, как запрашивать данные через концептуальную модель.

| Раздел | Описание |
| - | - |
| [Практическое руководство. Выполнение запросов к службе данных](/dotnet/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services) | Показано, как выполнять запросы к службе данных в приложении .NET. |
| [Практическое руководство. Спроецировать результаты запроса](/dotnet/framework/data/wcf/how-to-project-query-results-wcf-data-services) | Показано, как уменьшить объем данных, возвращаемых по запросу службы данных. |

 При использовании концептуальной модели, можно определить, какие данные является допустимым на языке, который совпадает с доменом. Можно определить допустимые данные в модели, или можно добавить проверку для операций, выполняемых в службе сущности или данных.

 Следующие разделы показывают, как добавить проверку в приложения служб WCF Data Services.

|Раздел|Описание|
|-----------|-----------------|
|[Практическое руководство. Перехват сообщений службы данных](/dotnet/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services)|Показано, как добавить проверку в операцию службы данных.|

 Следующие разделы показывают, как для создания, изменения и удаления данных, выполняя операции с сущностями.

|Раздел|Описание|
|-----------|-----------------|
|[Практическое руководство. Добавление, изменение и удаление сущностей](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)|Показано, как создание, обновление и удаление данных сущности в службе данных.|
|[Практическое руководство. Определение связей сущностей](/dotnet/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services)|Показано, как создать или изменить связи в службе данных.|

## <a name="see-also"></a>См. также

- [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Выполнение запросов к службе данных](/dotnet/framework/data/wcf/querying-the-data-service-wcf-data-services)