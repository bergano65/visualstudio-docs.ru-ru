---
title: "Расширение модели объекта базового проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b92fe7fece58dd2006507f0285d3c440af437ee4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-object-model-of-the-base-project"></a>Расширение модели объекта базового проекта
Подтип проекта может расширять объектную модель автоматизации базового проекта в следующих местах:  
  
-   Project.Extender («\<ProjectSubtypeName >») — это позволяет подтипом проекта предлагать объекта со специализированными методами из <xref:EnvDTE.Project>. Для предоставления подтипом проекта можно использовать расширения автоматизации `Project` объекта. <xref:EnvDTE80.IInternalExtenderProvider>Интерфейс, реализованный в инвентаризации подтип основного проекта должны обеспечивать его объект для `VSHPROPID_ExtObjectCATID` из <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (в зависимости от `itemid` значение VSITEMID_ROOT, из `VSITEMID`) CATID.  
  
-   ProjectItem.Extender («\<ProjectSubtypeName >»)-это позволяет подтипом проекта предлагать объекта со специализированными методами, определенной <xref:EnvDTE.ProjectItem> объекта в проекте. Подтип проекта расширители автоматизации можно использовать для предоставления этого объекта. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный в инвентаризации подтип основной проект должен предлагать его объект для `VSHPROPID_ExtObjectCATID` из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (соответствующее требуемой `VSITEMID`) CATID.  
  
-   Project.Properties - данная коллекция предоставляет независимые свойствах `Project` объекта. Дополнительные сведения о свойствах проекта см. в разделе <xref:EnvDTE.Project.Properties%2A>. Подтипом проекта расширители автоматизации можно использовать для добавления его свойства в эту коллекцию. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный в инвентаризации подтип основной проект должен предлагать его объект для `VSHPROPID_BrowseObjectCATID` из VSHPROPID2 (в зависимости от `itemid` значение VSITEMID_ROOT, из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.  
  
-   Configuration.Properties - это коллекция предоставляет зависимые свойства конфигурации проекта для определенной конфигурации (например, Debug). Для получения дополнительной информации см. <xref:EnvDTE.Configuration>. Подтипом проекта расширители автоматизации можно использовать для добавления его свойства в эту коллекцию. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный в средство инвентаризации программного обеспечения основной проект подтип предлагает его объект для CATID `VSHPROPID_CfgBrowseObjectCATID` (в зависимости от `itemid` значение <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Интерфейс используется для различения одной конфигурации объекта от другого.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>