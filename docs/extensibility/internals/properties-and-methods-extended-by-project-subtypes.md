---
title: Свойства и методы, расширенные по подтипам проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f5f67ac70b7ca6d5151a9115f20be88f6984d52
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725344"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Свойства и методы, расширенные подтипами проектов
Подтип проекта имеет множество возможностей для влияния на поведение проекта, поскольку он создается как агрегат базового проекта. В этом разделе перечислены некоторые функции, которые могут быть расширены или изменены подтипами проекта.

## <a name="features-gained-by-aggregation"></a>Функции, полученные в результате агрегирования
 В следующей таблице перечислены многие методы, которые агрегаты позволяют переопределять подтипы проектов в базовых проектах.

|Методы, переопределенные агрегатом|Подтип проекта|
|---------------------------------------|---------------------|
|Из <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Включение подтипа проекта для<br /><br /> — Изменение заголовка и значка узла проекта.<br />— Полностью переопределить объект `Browse` проекта.<br />— Определяет, можно ли переименовать проект.<br />— Порядок сортировки элемента управления.<br />— Управление контекстом пользователя для динамической справки.|
|Из <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Включает подтип проекта для управления тем, какие контекстные службы предоставляются конструкторам и редакторам.|
|Из <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Включение подтипа проекта для<br /><br /> — Участвовать в маршрутизации команд для команд проекта.<br />— Добавление, удаление и отключение команд окружения проекта и обозреватель решений активных команд.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Позволяет подтипу проекта фильтровать содержимое, отображаемое пользователем в диалоговом окне **Добавление нового элемента** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Включение подтипа проекта для<br /><br /> — Определение генератора по умолчанию по заданному расширению файла.<br />— Сопоставьте понятное имя генератора с COM-объектом.|

## <a name="properties-used-by-project-subtypes"></a>Свойства, используемые подтипами проектов
 Среда и базовая система проектов могут использовать свойства из <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> и <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> перечисления, описанные в следующей таблице, чтобы обеспечить подтип проекта для управления различными функциями системы проектов.

|ВШПРОПИД, свойство|Подтип проекта|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Позволяет подтипу проекта управлять содержимым диалогового окна **Добавление элемента** . Подтип проекта может предоставлять новую спецификацию каталогов шаблонов, добавлять новые виды элементов, удалять существующие элементы и реорганизовывать подмножество элементов в диалоговом окне **Добавление элемента** базового проекта.|
|`PropertyPagesCLSIDList`|Позволяет подтипу проекта добавлять или удалять страницы свойств, не зависящие от конфигурации.|
|`CfgPropertyPagesCLSIDList`|Позволяет подтипу проекта добавлять или удалять страницы свойств, зависящих от конфигурации.|
|`ExtObjectCATID`|Позволяет подтипу проекта предоставлять расширитель автоматизации для объектов проекта или элемента проекта, зная идентификатор CATID расширителя. Например, подтип проекта может предоставлять пользовательский объект `Project.Extender("<subtype>")`.|
|`BrowseObjectCATID`|Позволяет подтипу проекта предоставить расширитель автоматизации для объекта `Browse`, зная расширитель CATID. Например, подтип проекта может добавлять дополнительные свойства в коллекцию <xref:EnvDTE.Project.Properties%2A>.|
|`CfgBrowseObjectCATID`|Позволяет подтипу проекта предоставить расширитель автоматизации для объекта "Обзор конфигурации проекта". Например, подтип проекта может добавлять дополнительные свойства в коллекцию <xref:EnvDTE.Configuration.Properties%2A>.|
|`CfgExtObjectCATID`|Позволяет подтипу проекта предоставить расширитель автоматизации для объекта конфигурации.|
|`DefaultPlatformName`|Позволяет подтипу проекта определить имя платформы для объектов конфигурации проекта.|

 Базовый проект предоставляет реализацию указанных выше свойств по умолчанию. Базовый проект получает эти данные путем вызова `QueryInterface` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> для самого внешнего подтипа проекта, тем самым позволяя подтипу проекта переопределять реализацию свойств.

## <a name="see-also"></a>См. также
- [Разработка подтипов проекта](../../extensibility/internals/project-subtypes-design.md)