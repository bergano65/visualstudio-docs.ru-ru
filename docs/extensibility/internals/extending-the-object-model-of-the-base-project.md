---
title: Расширение типовой модели базового проекта (ru) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708400"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Расширить объектную модель базового проекта

Подтип проекта может расширить модель объекта автоматизации базового проекта в следующих местах:

- Project.Extender("\<ProjectSubtypeName>"): Это позволяет подтипу проекта предлагать объект <xref:EnvDTE.Project> с пользовательскими методами от объекта. Подтип проекта может использовать расширители автоматизации для разоблачения `Project` объекта. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный на основном агрегаторе подтипа проекта, `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> должен предложить `itemid` свой объект для (соответствующего значению [VSITEMID. Корень](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender("\<ProjectSubtypeName>"): Это позволяет подтипу проекта предлагать объект <xref:EnvDTE.ProjectItem> с пользовательскими методами из конкретного объекта в рамках проекта. Подтип проекта может использовать расширители автоматизации для разоблачения этого объекта. Интерфейс, <xref:EnvDTE80.IInternalExtenderProvider> реализованный на основном агрегаторе подтипа проекта, `VSHPROPID_ExtObjectCATID` должен <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> предложить свой <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>объект для (соответствующего желаемому) CATID.

- Project.Properties: Эта коллекция предоставляет независят `Project` от конфигурации свойства объекта. Дополнительные сведения о свойствах `Project` см. в разделе <xref:EnvDTE.Project.Properties%2A>. Подтип проекта может использовать расширители автоматизации для добавления своих свойств в эту коллекцию. Интерфейс, <xref:EnvDTE80.IInternalExtenderProvider> реализованный на основном агрегаторе подтипа проекта, `VSHPROPID_BrowseObjectCATID` должен <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> предложить `itemid` свой объект для от (соответствующего значению [VSITEMID. Корень](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: Эта коллекция предоставляет зависящие от конфигурации свойства проекта для определенной конфигурации (например, Debug). Для получения дополнительной информации см. <xref:EnvDTE.Configuration>. Подтип проекта может использовать расширители автоматизации для добавления своих свойств в эту коллекцию. Интерфейс, <xref:EnvDTE80.IInternalExtenderProvider> реализованный на основном агрегаторе подтипов проекта, `VSHPROPID_CfgBrowseObjectCATID` предлагает свой `itemid` объект для CATID (соответствует значению [VSITEMID. Корень](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> используется для различения одного объекта просмотра конфигурации от другого.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
