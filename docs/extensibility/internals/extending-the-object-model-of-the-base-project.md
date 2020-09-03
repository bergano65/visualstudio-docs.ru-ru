---
title: Расширение объектной модели базового проекта | Документация Майкрософт
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33186cd477ade7f562f6191393dabe8e94f4f194
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708400"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Расширение объектной модели базового проекта

Подтип проекта может расширить объектную модель автоматизации базового проекта в следующих местах:

- Project. Extender (" \<ProjectSubtypeName> "): позволяет подтипу проекта предлагать объект с пользовательскими методами из <xref:EnvDTE.Project> объекта. Подтип проекта может использовать расширители автоматизации для предоставления `Project` объекта. <xref:EnvDTE80.IInternalExtenderProvider>Интерфейс, реализованный на основе статистического выражения подтипа проекта, должен предоставлять свой объект для `VSHPROPID_ExtObjectCATID` FROM <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (соответствующий `itemid` значению [вситемид. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem. Extender (" \<ProjectSubtypeName> "): позволяет подтипу проекта предлагать объект с пользовательскими методами из определенного <xref:EnvDTE.ProjectItem> объекта в проекте. Подтип проекта может использовать расширители автоматизации для предоставления этого объекта. <xref:EnvDTE80.IInternalExtenderProvider>Интерфейс, реализованный на основном агрегаторе подтипа проекта, должен предоставлять свой объект для `VSHPROPID_ExtObjectCATID` из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (соответствующего нужному <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> ) CATID.

- Project. Properties: Эта коллекция предоставляет независимые от конфигурации свойства `Project` объекта. Дополнительные сведения о свойствах `Project` см. в разделе <xref:EnvDTE.Project.Properties%2A>. Подтип проекта может использовать расширители автоматизации для добавления его свойств в эту коллекцию. <xref:EnvDTE80.IInternalExtenderProvider>Интерфейс, реализованный на основном агрегаторе подтипа проекта, должен предоставлять свой объект для `VSHPROPID_BrowseObjectCATID` FROM <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (соответствующий `itemid` значению [вситемид. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration. Properties: Эта коллекция предоставляет зависящие от конфигурации свойства проекта для конкретной конфигурации (например, Debug). Для получения дополнительной информации см. <xref:EnvDTE.Configuration>. Подтип проекта может использовать расширители автоматизации для добавления его свойств в эту коллекцию. <xref:EnvDTE80.IInternalExtenderProvider>Интерфейс, реализованный на главном агрегаторе подтипа проекта, предлагает свой объект для CATID `VSHPROPID_CfgBrowseObjectCATID` (соответствующий `itemid` значению [вситемид. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Интерфейс используется для различения одного объекта обзора конфигурации из другого.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
