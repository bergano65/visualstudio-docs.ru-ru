---
title: Инвентаризация подготовительных сред | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 03/06/2020
ms.topic: conceptual
description: Узнайте об обязанностях администраторов проводить предварительную инвентаризацию
ms.openlocfilehash: dc307d9d2f83666c6648a35b3e28a81da2de5c38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80232758"
---
# <a name="inventory-of-pre-production-environment"></a>Инвентаризация подготовительной среды
Подписки на Visual Studio упрощают управление активами благодаря инвентаризации пользователей, а не устройств.

Администраторы Visual Studio должны назначать подписки на Visual Studio **конкретным пользователям по их именам**. Соглашения об именовании, такие как Dev1, Dev2, или использование названий команд, например FeatureTeam, **не допускаются**.

Вот ряд мер, позволяющих упростить инвентаризацию подготовительной среды:
- Проверьте назначения пользователей. Корпорация Майкрософт предоставляет веб-сайт под названием [Портал администрирования Visual Studio](https://manage.visualstudio.com/), чтобы помочь вам в отслеживании назначений подписок на Visual Studio.
- Используйте локальную или облачную службу Active Directory для инвентаризации пользователей. Если вы используете Active Directory для управления доступом пользователей к системам, на основе членства в каталоге можно определять пользователей, относящихся к группам разработки и тестирования.
- Используйте автоматические средства для инвентаризации систем. Вам также может потребоваться использовать средство инвентаризации ПО для управления активами программного обеспечения и разделения подготовительных и рабочих сред. Многие клиенты, использующие Microsoft System Center, создают соглашения об именовании для автоматизации этого этапа процесса инвентаризации.
- Получите помощь при проведении согласования вручную. Назначьте сотрудников, которые будут помогать вам при согласовании пользователей среды разработки и тестирования.

## <a name="resources"></a>Ресурсы
- [Документ по лицензированию Visual Studio](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Поддержка по администрированию и подпискам Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Условия корпоративного лицензирования](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>См. также раздел
- [Документация по Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Документация по Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Документация по Azure](https://docs.microsoft.com/azure/)
- [Документация по Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Дальнейшие действия
Узнайте больше об обязанностях администраторов:
- [Обязанности администратора](admin-responsibilities.md)
- [Управление большими рабочими группами и сторонними подрядчиками](manage-teams.md)
- [Отслеживание назначений пользователей и обработка заказов](assignments-orders.md)
- Используйте [Максимальное использование](maximum-usage.md) для учета обязательств по покупке



