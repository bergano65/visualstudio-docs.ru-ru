---
title: Вклад в автоматизацию модели (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d660edc740229c3e91b99e1f59eb37b4e9312098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709271"
---
# <a name="contribute-to-the-automation-model"></a>Внести свой вклад в модель автоматизации
Visual Studio предоставляет набор интерфейсов автоматизации для настройки среды. Модель автоматизации — это объектная модель, которая позволяет конечным пользователям создавать надстройки и расширения Visual Studio.

 Кроме того, вам, как разработчику VSPackage, уместно внести свой вклад в модель автоматизации; делая это, вы позволяете конечным пользователям вашего VSPackage создавать надстройки и, как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]правило, обеспечивают согласованный опыт работы модели пользователя, когда они используют ваш VSPackage в .

 Чтобы сделать конечный пользовательский опыт последовательным, вы можете следовать набору руководящих принципов, как вы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]проектируете ваш VSPackage так, что модель автоматизации для вашего VSPackage следует идеи в .

## <a name="in-this-section"></a>В этом разделе
- [Обзор модели автоматизации](../../extensibility/internals/automation-model-overview.md)

 Определяет модель автоматизации как связанные группы объектов, контролирующих основные аспекты общей среды. Этот набор объектов изображен на диаграмме модели автоматизации.

- [Обеспечить автоматизацию ДЛЯ VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)

 Обсуждается два основных способа обеспечения автоматизации вашего VSPackage.

- [Экспозиция объектов проекта](../../extensibility/internals/exposing-project-objects.md)

 Предоставляет пошаговые инструкции для создания объектов, специфиченных для VSPackage.

- [Моделирование проектов](../../extensibility/internals/project-modeling.md)

 Объясняет стандартные объекты проекта, необходимые для создания автоматизации для нового типа проекта, и иллюстрирует путь автоматизации проекта. В этой теме также приводятся списки деклараций и реализации для классов.

- [Разоблачение событий](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Предоставляет пошаговые инструкции по созданию событий для модели автоматизации.

- [Поддержка автоматизации страниц опционов](../../extensibility/internals/automation-support-for-options-pages.md)

 Описывает, как вернуть объект автоматизации для поддержки свойств **пользовательского** диалогового окна VSPackage `DTE.Properties` в меню **Tool** путем расширения объекта.

- [Обеспечить автоматизацию кода](../../extensibility/internals/providing-automation-for-code.md)

 Объясняет, что создание модели автоматизации для кода не требуется. Тем не менее, ссылка предоставляется в этой теме, которая обеспечивает проницательную информацию в моделях кода.

- [Как: Обеспечить автоматизацию Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Объясняет, что автоматизация — хорошая идея, когда вы хотите сделать объекты автоматизации доступными на окне, а среда уже не предоставляет готовый объект автоматизации. Обсуждается автоматизация окон инструментов и документооборота.

- [Использование модели автоматизации](../../extensibility/internals/using-the-automation-model.md)

 Приводит два примера кода, которые показывают, как потребитель автоматизации получает начальные объекты автоматизации проекта.

- [Автоматизация для объектов конфигурации и SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Предоставляет информацию об автоматизации для объектов configuration и SelectedItems.

## <a name="reference"></a>Справочник
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>Предоставляет образец кода, который показывает, как VSPackage участвует в модели объектов автоматизации DTE. Списки параметров, значений возврата и выбранных замечаний.
