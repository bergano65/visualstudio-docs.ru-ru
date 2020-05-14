---
title: Свойства и методы, расширенные подтипами проекта Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9963f779055fcf1ed0efd8c47abbe1cce35631a6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706199"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Свойства и методы, расширенные подтипами проектов
Подтип проекта обладает большой силой, чтобы влиять на поведение проекта, поскольку он построен как агрегатор базового проекта. В этом разделе кратко излагаются некоторые функции, которые могут быть улучшены или изменены подтипами проекта.

## <a name="features-gained-by-aggregation"></a>Особенности, полученные от агрегации
 В следующей таблице кратко излагаются многие методы, которые агрегация позволяет подтипам проектов переопределятьв в базовых проектах.

|Методы, переоверченные агрегацией|Подтип проекта|
|---------------------------------------|---------------------|
|От: <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Позволяет подтипу проекта<br /><br /> - Изменение подписи и значок узла проекта.<br />- Полностью `Browse` переопределить объект проекта.<br />- Контролируйте, можно ли переименовать проект.<br />- Контроль сортировки порядка.<br />- Управление пользовательским контекстом для динамической помощи.|
|От: <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Позволяет подтипу проекта контролировать, какие контекстные услуги предоставляются дизайнерам и редакторам.|
|От: <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Позволяет подтипу проекта<br /><br /> - Участвуйте в командной реукторе для команд проекта.<br />- Добавляйте, удаляйте или отменяйте как команды по эмбиенту проекта, так и активные команды Solution Explorer.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Позволяет подтипу проекта фильтровать то, что пользователь видит в диалоговом поле **Add New Item.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Позволяет подтипу проекта<br /><br /> - Определите генератор по умолчанию с учетом расширения файла.<br />- Карта человека читаемый генератор имя объекта COM.|

## <a name="properties-used-by-project-subtypes"></a>Свойства, используемые подтипами проектов
 Система проекта среды и базы <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> может <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> использовать свойства из и перечисления, описанные в следующей таблице, чтобы позволить подтипу проекта управлять различными функциями проектной системы.

|Имущество ВШПРОПИД|Подтип проекта|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Позволяет подтипу проекта контролировать содержимое диалогового окна **Добавить элемент.** Подтип проекта может предоставить новую спецификацию каталогов шаблонов, добавить новые виды элементов, удалить существующие элементы и реорганизовать подмножество элементов в диалоговом окне **добавленного элемента** базового проекта.|
|`PropertyPagesCLSIDList`|Позволяет подтипу проекта добавлять или удалять страницы свойств, не зависят от конфигурации.|
|`CfgPropertyPagesCLSIDList`|Позволяет подтипу проекта добавлять или удалять страницы свойств, зависящих от конфигурации.|
|`ExtObjectCATID`|Позволяет подтипу проекта предоставить расширитель автоматизации для объектов проекта или элемента проекта, зная catID расширения. Например, подтип проекта может `Project.Extender("<subtype>")` предоставить пользовательский объект.|
|`BrowseObjectCATID`|Позволяет подтипу проекта обеспечить расширитель автоматизации для `Browse` объекта, зная Extender CATID. Например, подтип проекта может добавить <xref:EnvDTE.Project.Properties%2A> дополнительные свойства в коллекцию.|
|`CfgBrowseObjectCATID`|Позволяет подтипу проекта обеспечить расширитель автоматизации для объекта просмотра конфигурации проекта. Например, подтип проекта может добавить <xref:EnvDTE.Configuration.Properties%2A> дополнительные свойства в коллекцию.|
|`CfgExtObjectCATID`|Позволяет подтипу проекта предоставить расширитель автоматизации для объекта конфигурации.|
|`DefaultPlatformName`|Позволяет подтипу проекта определить название платформы для объектов конфигурации проекта.|

 Базовый проект обеспечивает реализацию вышеуказанных свойств по умолчанию. Базовый проект получает `QueryInterface` их, вызывая <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> на внешний подтип проекта, что позволяет подтипу проекта переопределить реализацию свойств.

## <a name="see-also"></a>См. также
- [Разработка подтипов проекта](../../extensibility/internals/project-subtypes-design.md)
