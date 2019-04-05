---
title: Расширение модели объекта базового проекта | Документация Майкрософт
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
ms.openlocfilehash: 69ad1b421e648c5248501ebdf76f97fab7f3a66e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979579"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Расширение модели объекта базового проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Подтип проекта может расширить объектную модель автоматизации базового проекта в следующих местах:  
  
-   Project.Extender («\<ProjectSubtypeName > ") — это позволяет подтипом проекта, пройдя пользовательских методов из объекта <xref:EnvDTE.Project>. Подтип проекта расширители автоматизации можно использовать для предоставления `Project` объекта. <xref:EnvDTE80.IInternalExtenderProvider>Интерфейс, реализованный в главный проект подтип средства инвентаризации программного обеспечения следует предлагать свой объект для `VSHPROPID_ExtObjectCATID` из <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (соответствующий `itemid` значение VSITEMID_ROOT из `VSITEMID`) CATID.  
  
-   ProjectItem.Extender («\<ProjectSubtypeName > ") — это позволяет подтипом проекта, пройдя пользовательских методов объекта от конкретного <xref:EnvDTE.ProjectItem> объекта в проекте. Подтип проекта можно использовать расширения автоматизации для предоставления этого объекта. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный в главный проект подтип средства инвентаризации программного обеспечения необходимо предложить свой объект для `VSHPROPID_ExtObjectCATID` из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (соответствующий требуемой `VSITEMID`) CATID.  
  
-   Project.Properties — данная коллекция предоставляет независимым свойствах `Project` объекта. Дополнительные сведения о свойствах проекта, см. в разделе <xref:EnvDTE.Project.Properties%2A>. Подтип проекта можно использовать расширения автоматизации для добавления его свойства в данную коллекцию. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный в главный проект подтип средства инвентаризации программного обеспечения необходимо предложить свой объект для `VSHPROPID_BrowseObjectCATID` из VSHPROPID2 (соответствующий `itemid` значение VSITEMID_ROOT из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.  
  
-   Configuration.Properties — это коллекция предоставляет зависимые свойства конфигурации проекта для конкретной конфигурации (например, Debug). Для получения дополнительной информации см. <xref:EnvDTE.Configuration>. Подтип проекта можно использовать расширения автоматизации для добавления его свойства в данную коллекцию. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный в главный проект подтип средства инвентаризации программного обеспечения предлагает свой объект для этого идентификатор CATID `VSHPROPID_CfgBrowseObjectCATID` (соответствующий `itemid` значение <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Интерфейс используется для различения один объект обзора конфигурации из другого.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
