---
title: Расширение системы проектов SharePoint | Документация Майкрософт
description: Расширение системы проектов SharePoint. Узнайте, как расширить систему проектов SharePoint. Общие сведения о типичных задачах разработки.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5a81fef67cc6816f16a074494005a61d647abeab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889685"
---
# <a name="extend-the-sharepoint-project-system"></a>Расширение системы проектов SharePoint
  Решения SharePoint можно создавать с помощью набора шаблонов проектов и шаблонов элементов в Visual Studio. Эти шаблоны соответствуют требованиям многих сценариев разработки, но в некоторых случаях они не предоставляют нужных функциональных возможностей. В таких случаях можно расширить систему проектов SharePoint.

## <a name="overview-of-the-sharepoint-project-system"></a>Общие сведения о системе проектов SharePoint
 Система проектов SharePoint основана на фундаментальном компоненте *элементов проектов SharePoint*. Элемент проекта SharePoint представляет одну настройку SharePoint, например определение списка, веб-часть или тип содержимого.

 Проект SharePoint — это проект Visual Studio, который содержит один или несколько элементов проекта SharePoint. Проекты SharePoint также содержат дополнительные компоненты, определяющие группирование элементов проекта в компоненты и пакеты для развертывания.

 Дополнительные сведения о содержимом элементов проектов SharePoint и проектов SharePoint см. в разделе [Создание шаблонов элементов и шаблонов проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="how-to-extend-the-sharepoint-project-system"></a>Расширение системы проектов SharePoint
 Расширить систему проектов SharePoint можно следующими способами.

- Определите собственные типы элементов проектов SharePoint и свяжите их с новыми шаблонами элементов или шаблонами проектов в Visual Studio. Например, можно определить тип элемента проекта SharePoint для создания настраиваемого действия или поля. Дополнительные сведения см. в разделе [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).

- Расширение типов элементов проектов SharePoint, уже установленных в Visual Studio. Например, можно добавить пункт контекстного меню в элемент проекта в **Обозреватель решений** и настроить элемент проекта, когда разработчик выберет пункт меню. Дополнительные сведения см. в разделе [расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md).

- Расширение проектов SharePoint. Например, можно добавить обработчики событий для выполнения конкретных задач при добавлении или удалении элементов из проектов SharePoint. Дополнительные сведения см. в разделе [расширение проектов SharePoint](../sharepoint/extending-sharepoint-projects.md).

- Расширяйте поведение упаковки и развертывания элементов проектов SharePoint и проектов SharePoint. Например, можно создать собственные шаги развертывания для выполнения при развертывании или отзыве проекта, а также выполнять дополнительные пользовательские задачи, когда Visual Studio выполняет определенные шаги развертывания. Дополнительные сведения см. в разделе [Расширение упаковки и развертывания SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

## <a name="common-development-tasks"></a>Общие задачи разработки
 В расширениях системы проектов SharePoint можно выполнять следующие стандартные задачи:

- Сохранение пользовательских строковых данных с помощью элементов проекта и нескольких разных типов файлов проекта. Дополнительные сведения см. [в разделе Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

- Преобразование объекта в системе проектов SharePoint в соответствующий объект в объектной модели автоматизации Visual Studio или объектной модели интеграции или наоборот. Дополнительные сведения см. в разделе [преобразовать между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

## <a name="see-also"></a>См. также раздел
- [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Расширение проектов SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Расширение упаковки и развертывания SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Расширение средств SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Основные понятия и функции программирования для расширений инструментов SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
