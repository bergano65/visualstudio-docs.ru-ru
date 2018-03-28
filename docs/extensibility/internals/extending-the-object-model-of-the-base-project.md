---
title: Расширение модели объекта базового проекта | Документы Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a0fdda35744aaddf8789818afd1f938897470147
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="extending-the-object-model-of-the-base-project"></a>Расширение модели объекта базового проекта

Подтип проекта может расширять объектную модель автоматизации базового проекта в следующих местах:

-   Project.Extender («\<ProjectSubtypeName >») — это позволяет подтипом проекта предлагать объекта со специализированными методами из <xref:EnvDTE.Project>. Для предоставления подтипом проекта можно использовать расширения автоматизации `Project` объекта. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный в инвентаризации подтип основного проекта должны обеспечивать его объект для `VSHPROPID_ExtObjectCATID` из <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (в зависимости от `itemid` значение [VSITEMID. Корневой](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)) CATID.

-   ProjectItem.Extender («\<ProjectSubtypeName >»)-это позволяет подтипом проекта предлагать объекта со специализированными методами, определенной <xref:EnvDTE.ProjectItem> объекта в проекте. Подтип проекта расширители автоматизации можно использовать для предоставления этого объекта. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный в инвентаризации подтип основной проект должен предлагать его объект для `VSHPROPID_ExtObjectCATID` из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (соответствующее требуемой <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID.

-   Project.Properties - это коллекция предоставляет свойства зависят от конфигурации `Project` объекта. Дополнительные сведения о свойствах проекта см. в разделе <xref:EnvDTE.Project.Properties%2A>. Подтипом проекта расширители автоматизации можно использовать для добавления его свойства в эту коллекцию. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный в инвентаризации подтип основной проект должен предлагать его объект для `VSHPROPID_BrowseObjectCATID` из VSHPROPID2 (в зависимости от `itemid` значение [VSITEMID. Корневой](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>), из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.

-   Configuration.Properties - эта коллекция предоставляет зависящие от конфигурации свойства проекта для определенной конфигурации (например, Debug). Дополнительные сведения см. в разделе <xref:EnvDTE.Configuration>. Подтипом проекта расширители автоматизации можно использовать для добавления его свойства в эту коллекцию. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный в средство инвентаризации программного обеспечения основной проект подтип предлагает его объект для CATID `VSHPROPID_CfgBrowseObjectCATID` (в зависимости от `itemid` значение [VSITEMID. Корневой](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Интерфейс используется для различения одной конфигурации объекта от другого.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>