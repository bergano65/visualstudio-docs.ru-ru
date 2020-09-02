---
title: Расширение объектной модели базового проекта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7723881bce81824b66a936793175077a0ec67666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187170"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Расширение модели объекта базового проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Подтип проекта может расширить объектную модель автоматизации базового проекта в следующих местах:  
  
- Project. Extender (" \<ProjectSubtypeName> ") — позволяет подтипу проекта предлагать объект с пользовательскими методами из <xref:EnvDTE.Project> . Подтип проекта может использовать расширители автоматизации для предоставления `Project` объекта. <xref:EnvDTE80.IInternalExtenderProvider>Интерфейс, реализованный в агрегате агрегатора подтипа проекта, должен предоставлять свой объект `VSHPROPID_ExtObjectCATID` из <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (соответствующего `itemid` значению VSITEMID_ROOT, FROM `VSITEMID` ) CATID.  
  
- ProjectItem. Extender (" \<ProjectSubtypeName> ") — позволяет подтипу проекта предлагать объект с пользовательскими методами из определенного <xref:EnvDTE.ProjectItem> объекта в проекте. Подтип проекта может использовать расширители автоматизации для предоставления этого объекта. <xref:EnvDTE80.IInternalExtenderProvider>Интерфейс, реализованный на основном агрегаторе подтипа проекта, должен предоставлять свой объект для `VSHPROPID_ExtObjectCATID` из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (соответствующего нужному `VSITEMID` ) CATID.  
  
- Project. Properties — эта коллекция предоставляет независимые от конфигурации свойства `Project` объекта. Дополнительные сведения о свойствах проекта см. в разделе <xref:EnvDTE.Project.Properties%2A> . Подтип проекта может использовать расширители автоматизации для добавления его свойств в эту коллекцию. <xref:EnvDTE80.IInternalExtenderProvider>Интерфейс, реализованный на основном агрегаторе подтипа проекта, должен предоставлять свой объект `VSHPROPID_BrowseObjectCATID` из VSHPROPID2 (соответствующего `itemid` значению VSITEMID_ROOT, FROM <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> ) CATID.  
  
- Configuration. Properties — эта коллекция предоставляет зависящие от конфигурации свойства проекта для конкретной конфигурации (например, Debug). Для получения дополнительной информации см. <xref:EnvDTE.Configuration>. Подтип проекта может использовать расширители автоматизации для добавления его свойств в эту коллекцию. <xref:EnvDTE80.IInternalExtenderProvider>Интерфейс, реализованный на главном агрегаторе подтипа проекта, предлагает свой объект для CATID `VSHPROPID_CfgBrowseObjectCATID` (соответствующий `itemid` значению <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> ). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Интерфейс используется для различения одного объекта обзора конфигурации из другого.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
